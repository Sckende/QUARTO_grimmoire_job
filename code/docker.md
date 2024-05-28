---
title: 🐋 Docker
---

<img src="https://oneclick-cloud.com/wp-content/uploads/2023/08/Bigstock_-139961875-Docker-Emblem.-A-Blue-Whale-With-Several-Containers.-e1574090673987-1.jpg" width=75%>

# Environnement R dans Docker

[**The Rocker Project**](https://rocker-project.org/) propose une liste de repos Rocker disponibles avec différentes configurations d'environnement selon les besoins ([DockerHub page](https://hub.docker.com/u/rocker)).

Pour commencer, dans le terminal:

```bash
docker run --rm -ti r-base # création et lancement d'un environnement contenant base r
```

# Comment déployer R dans docker

[Running tour R script in Docker](https://www.statworx.com/en/content-hub/blog/running-your-r-script-in-docker/)  
L'objectif de ce tutotriel est l'automatisation de l'excécution d'un script R, sans nécessité d'avoir une interface utilisateur, car c'est le même script qui est relancé à un intervalle défini.

# Comment déployer une shiny app dans un Docker

[How To Dockerize ShinyApps](https://www.statworx.com/en/content-hub/blog/how-to-dockerize-shinyapps/)
