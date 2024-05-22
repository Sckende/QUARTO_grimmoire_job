---
title: 💡 Astuces
---

# Grappes de calcul - Alliance Canada

## Récupérer les tâches échouées et les relancer

Il s'agit d'une solution "à la mitaine" qui peut être remplacée par l'utilisation de l'outil [META-Farm](https://docs.alliancecan.ca/wiki/META-Farm) de l'Alliance.

<u>Mise en contexte</u>

On veut calculer le PCI pour plusieurs espèces. Initialement le array range allait de 1-243, ce qui correspondait aux 243 espèces. Après le premier lancement du script, 33 espèces (ou tâches) avaient échouées:

- Récupérer le statut des tâches (`sjobexitmod`)
- Récupérer les lignes qui présentent le pattern `FAILED` (`grep`)
- Récupérer la première colonnes qui contient `jobId_taskId` (`awk`)
- Couper les strings au niveau de `_` et récupérer la deuxième partie de string qui correspond à la tâche ID (`cut`)
- Enregistrer la sortie dans un fichier (`>`)

```bash
sjobexitmod -l jobId > sjobexitmod_status.txt
grep -e 'FAILED' sjobexitmod_status.txt | awk '{print $1}' | cut -d '_' -f 2 > failed_task_id.txt
```

- Dans le fichier bash envoyé à l'ordonnanceur slurm, créer une variable shell qui pourra être importé dans l'environnement `R`.

```bash
#!/bin/bash
#SBATCH --account=def-dgravel
#SBATCH --array=1-33
#SBATCH -t 01:00:00
#SBATCH --mem-per-cpu=50GB
#SBATCH --cpus-per-task=1
#SBATCH --job-name=Summer_school_test
#SBATCH --mail-user=juhc3201@usherbrooke.ca
#SBATCH --mail-type=ALL

echo $SLURM_ARRAY_TASK_ID

FAILED_TASK_ID=$(sed -n "${SLURM_ARRAY_TASK_ID}p" failed_task_id.txt)

echo $FAILED_TASK_ID

module load StdEnv/2023 gcc/12.3 gdal/3.7.2 arrow/15.0.1 udunits/2.2.28 r/4.4.0
Rscript pci.r
```

```r
failed_task_id <- as.integer(Sys.getenv("FAILED_TASK_ID")) #récupère la variable shell FAILED_TASK_ID
```

Ici la taille de l'array correspond au nombre de tâches qui ont échoué. `sed` permet de récupérer la valeur dans le fichier `failed_task_id.txt` qui correspond au numéro du `SLURM_ARRAY_TASK_ID`. Et cette `task_id` est utilisée pour indexer le nom de l'espèce qui manque (dans cet exemple).
