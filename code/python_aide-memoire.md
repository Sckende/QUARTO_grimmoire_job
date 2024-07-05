---
title: 🐍 Python
---

# Mots réservés ou mots clés au langage `Python`

Certains mots font partie du langage Python, et ne peuvent pas être utilisés comme noms de variables. Par exemple, `def`, `match`, `case`, `_`, `del` , `if`, `else`, `break` & `continue`.

# Création d'objets

## Listes

```python
list=[el1, el2, el3, ...]
```

## Tuples

Similaire aux listes mais non modifiables et définit avec `()` au lieu de `[]`.

```python
tuple=(el1, el2, el3, ...)
```

## Dictionnaires

Un dictionnaire est une structure de données qui enregistre des données dans des paires **clés-valeurs**. Un dictionnaire est défini à l'aide des `{}`.

![](https://user.oc-static.com/upload/2023/04/29/16827780421019_image9.png)

```Python
nouvelle_campagne = {
"responsable_de_campagne": "Jeanne d'Arc",
"nom_de_campagne": "Campagne nous aimons les chiens",
"date_de_début": "01/01/2020",
"influenceurs_importants": ["@MonAmourDeChien", "@MeilleuresFriandisesPourChiens"]
}
```

La fonction `dict()` peut aussi être utilisée.

```Python
d = dict([
    (<key>, <value>),
    (<key>, <value),
      .
      .
      .
    (<key>, <value>)
])
```

Une valeur peut être un objet complexe telle qu'une liste.
Il est possible de modifier le dictionnaire après sa création.

```python
# creation dictionnaire
infos_labradoodle = {
    "poids": "13 à 16 kg",
    "origine": ["États-Unis", "Canada"]
}

# Ajout d'une paire clé-valeur
infos_labradoodle["nom_scientifique"]="Canis lupus familiaris"

# Appel des valeurs associées à origine
print(infos_labradoodle["origine"]) # ["États-Unis", "Canada"]
print(infos_labradoodle["origine"][0]) # Canada

# Suppression d'une association clé-valeur avec l'utilisation d'un mot clé del
del infos_labradoodle["nom_scientifique"] # retrait de l'association nom_scientifique - Canis lupus familiaris
del infos_labradoodle["origine"][0] # retrait de la première valeur associée à origine

# Vérification de l'existence d'une clé

print("poids" in infos_labradoodle) # True
print("race" in infos_labradoodle) # False

```

# Indexation

Les éléments d'une liste (ou d'un tuple) peuvent être indexés en partant du premier élément `[0]` ou en partant du dernier `[-1]`.

```python
list=[el1, el2, el3, ...]
list[0] # el1
list[-2] #el2
```

# Méthodes

Une méthode est une façon de réaliser une opération spécifique sur un élément.

## Méthodes les plus courantes associées aux listes

| méthode     | définition                                                                                               |
| ----------- | -------------------------------------------------------------------------------------------------------- |
| `extend()`  | Ajoute plusieurs éléments à la fin                                                                       |
| `insert()`  | Insère un élément à une position donnée                                                                  |
| `pop()`     | Supprime et renvoie l'élément à une position donnée ou le dernier élément si aucun indice n'est spécifié |
| `index()`   | Renvoie la première occurrence de l'élément spécifié                                                     |
| `count()`   | Renvoie le nombre d'occurrences de l'élément spécifié                                                    |
| `reverse()` | Inverse l'ordre des éléments                                                                             |

```python
list=[el1, el2, el3]
list.append(el4) # el1, el2, el3, el4
list.reverse() # el4, el3, el2, el1
```

Cf documentation python sur les [méthodes](https://docs.python.org/fr/3/tutorial/datastructures.html).

## Méthodes les plus courantes associées aux dictionnaires

| méthode    | définition                                                                                                                             |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| `keys()`   | ​​Retourne une vue sur les clés du dictionnaire                                                                                        |
| `values()` | Retourne une vue sur les valeurs du dictionnaire                                                                                       |
| `items()`  | Retourne une vue sur les couples (clé, valeur) du dictionnaire                                                                         |
| `get(clé)` | Retourne la valeur associée à la clé spécifiée. Si la clé n'est pas présente dans le dictionnaire, retourne la valeur `None`           |
| `pop(clé)` | Supprime la clé spécifiée et retourne la valeur associée. Si la clé n'est pas présente dans le dictionnaire, retourne la valeur `None` |
| clear()    | Supprime tous les éléments du dictionnaire                                                                                             |

# Boucles

## `if`/`elif`/`else`

Les instructions `if`/`elif`/`else` permettent de définir des conditions multiples. Le mot-clé `elif` vous permet d’ajouter autant de conditions que vous voulez. Vous devez ensuite terminer avec une instruction `else`. Les opérateurs logiques `and`, `or`, `not` peuvent être utilisés pour vérifier des conditions multiples au sein d'une même instructions.

```python
fruit = "pomme"
if fruit=="pomme":
    print("J'aime les pommes !")
elif fruit=="banane":
    print("J'aime les bananes !")
elif fruit=="orange":
    print("Les oranges sont bonnes pour la santé.")
else :
    print("Je ne connais pas ce fruit.")
```

Afin de rendre plus lisible ce genre de boucle, les `match cases` peuvent être utilisés.

```python
match fruit:
    case "pomme":
        print("J'aime les pommes !")
    case "banane":
        print("Je n'aime pas les bananes.")
    case "orange":
        print("Les oranges sont bonnes pour la santé.")
    case _:
        print("Je ne connais pas ce fruit.")
```

## `for`

```python
races_de_chien = ["golden retriever", "chihuahua", "terrier", "carlin"]
for chien in races_de_chien:
    print(chien)
```

## `while`

```python
capacite_maximale = 10
capacite_actuelle = 3
while capacite_actuelle < capacite_maximale:
    capacite_actuelle += 1
```

## Plusieurs listes en même temps

S'il est nécessaire de traiter deux (ou plus) listes en même temps dans une boucle, il est possible d'utiliser la fonction `zip()`.

```python
listA = ["pomme", "poire", "pêche"]
listB = [2, 5, 1]

for val1, val2 in zip(listA, listB):
    print(val2, '\t',  val1)

# 2        pomme
# 5        poire
# 1        pêche
```

# Afficher des variables - la `f-string`

Pour afficher des variables, la `f-string` est souvent utilisée car elle permet d'insérer facilement les variables dans la chaîne de caractères à afficher. Une `f-string` est une chaîne de caractères précédée d'un `f` (ou `F`), et contenant des expressions entre accolades `{}` qui seront évaluées lors de l'exécution du programme.

```python
nom = Pouet
prenom = Naty
age = 2.5

print(f"Je m'appelle {prenom} {nom} et j'ai {age} ans.")

# Je m'appelle Naty Pouet et j'ai 2.5 ans.
```
