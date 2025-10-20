[[Numpy]]   [[Pandas]]   [[Matplotlib]]
[[Flask]]  [[Python/SQLITE]]  [[Pygame]]  [[django]]
[[Programmation Orientée Objet]]
[[Environnement virtuel Python]] [[pip]]

Pour savoir où python est installé :``which python`` ou `where python`


![cheatsheet](https://prog.connect4techs.com/beginners-python-cheat-sheet/)
![](https://prog.connect4techs.com/beginners-python-cheat-sheet/)

| Symbole               | Effet                           | Raccourci Mac     |
| --------------------- | ------------------------------- | ----------------- |
| `#`                   | commentaire sur une ligne       |                   |
| `''' bla bla bla '''` | commentaire de plusieurs ligne  |                   |
| `\`                   | saut à la ligne dans le code    | `alt`+`shift`+`/` |
| `\n`                  | saut à la ligne dans une string |                   |
```python
# Commentaire sur une seule ligne  
  
"""
Commentaire
sur plusieurs lignes.
"""

'''
On peut aussi utiliser des apostrophes pour des commentaires
sur plusieurs lignes.
'''
```
 

---
## Un langage interprété :  

code source lu ligne par ligne  >  interpréteur  >   donnée de sortie

python est sensible :
-  à l’indentation (elle permet d’entrer dans la fonction)
- à la casse

## Les langages compilés :
code source > Compilateur > …  > donnée de sortie

Les langages compilés sont directement transformés en code machine après l'écriture.  
Passe d'un code lisible par un humain à du binaire.  
Grâce à ce système, ils sont beaucoup plus rapide que les langages compilés

## Modules
- ensemble de fichiers .py contenant des fonctions, des classes, ou encore des variables pouvant être appelé dans le code.
- Quand un programme devient conséquent, il est recommandé de ranger les fonctions dans des fichiers .py séparés (modules) que l'on appelle dans le fichier principal :
 ```python
import mon_module
mon_module.ma_fonction()

# ou bien
import mon_module as m
m.ma_fonction()

# on peut n'importer qu'une seule fonction du module
from mon_module import ma_fonction
# cela permet de l'instancier sans spécifier le module source
ma_fonction()
```

##### On peut exécuter le module dans la console (terminal) :  
  
```bash
# Lance l'interpréteur python et exécute le fichier.py
python3 “fichier.py ”

# Quitte l'interpréteur python
exit()
```



##### Bonne pratique : dossier 'module' avec 1 fichier`__init__`

Mettre les modules secondaires dans un dossier avec un fichier `__init__`

Le fichier `__init__.py` est utilisé dans les packages Python pour indiquer que le dossier contenant ce fichier doit être traité comme un package. 

- **Initialisation de module** :
  Il peut contenir du code d'initialisation qui s'exécute lorsque le package est importé. Cela peut inclure la configuration de variables globales ou l'importation de modules.

- **Création de sous-packages** :
  Il permet d'organiser le code en sous-packages, facilitant ainsi la structure de votre projet.

- **Contrôle de l'importation** :
  Vous pouvez définir ce qui est accessible lorsque vous importez le package. Par exemple, vous pouvez spécifier quels modules ou classes doivent être importés par défaut.


Python définit deux types de paquets :

- les [paquets classiques](https://docs.python.org/fr/3/glossary.html#term-regular-package) 
Paquets traditionnels tels qu'ils existaient dans Python 3.2 et antérieurs.
Un paquet classique est typiquement implémenté sous la forme d'un répertoire contenant un fichier `__init__.py`. Quand un paquet classique est importé, ce fichier `__init__.py` est implicitement exécuté.
  
Par exemple, l'arborescence suivante définit un paquet `parent` au niveau le plus haut avec trois sous-paquets :

parent/
    __init__.py
    one/
        __init__.py
    two/
        __init__.py
    three/
        __init__.py

Importer `parent.one` exécute implicitement `parent/__init__.py` et `parent/one/__init__.py`.
Les importations postérieures de `parent.two` ou `parent.three` exécutent respectivement `parent/two/__init__.py` ou `parent/three/__init__.py`

- les [paquets espaces de nommage](https://docs.python.org/fr/3/glossary.html#term-namespace-package)

## types de donnée
![data structure](img/python/python_data_structure.jpeg)

immutable : ne peut pas être changé après avoir été créé
```python
# une string est immutable
my_string = 'brain'
# on ne pas modifier 'brain' en 'train'
my_string[0] = 't'    ! error !
# On peut réassigner une autre string à la variable
my_string = 'train'
```

| **Catégorie**         | **Type**     | **Description**                | **Exemple**                  | **Mutabilité**      |
| --------------------- | ------------ | ------------------------------ | ---------------------------- | ------------------- |
| **Types Numériques**  | `int`        | Entiers                        | 3, -5, 42                    | Immuable            |
|                       | `float`      | Nombres à virgule flottante    | 3.14, -0.001, 2.0            | Immuable            |
|                       | `complex`    | Nombres complexes              | 1+2j, -3+4j                  | Immuable            |
| **Types de Séquence** | `str`        | Chaînes de caractères          | "hello", 'Python'            | Immuable            |
|                       | `list`       | Listes                         | [1, 2, 3], ['a', 'b', 'c']   | Mutable             |
|                       | `tuple`      | Tuples                         | (1, 2, 3), ('a', 'b', 'c')   | Immuable            |
|                       | `range`      | Plages de nombres              | range(10), range(1, 5, 2)    | Immuable            |
| **Types de Mappage**  | `dict`       | Dictionnaires                  | {'name': 'Alice', 'age': 25} | Mutable             |
| **Types d'Ensemble**  | `set`        | Ensembles                      | {1, 2, 3}, {'a', 'b', 'c'}   | Mutable             |
|                       | `frozenset`  | Ensembles immuables            | frozenset([1, 2, 3])         | Immuable            |
| **Types Booléens**    | `bool`       | Booléens                       | True, False                  | Immuable            |
| **Types Binaires**    | `bytes`      | Séquences d'octets immuables   | b'hello'                     | Immuable            |
|                       | `bytearray`  | Séquences d'octets modifiables | bytearray(b'hello')          | Mutable             |
|                       | `memoryview` | Vues sur les objets en mémoire | memoryview(bytes(5))         | Dépend de la source |
| **Types Spéciaux**    | `NoneType`   | Le type de l'objet `None`      | None                         | Immuable            |
liste : on y met ce qu'on veux, mmodifiable, on peut ajouter des element
tuple  : comme une liste mais les elements ne sont pas modifiable, on ne peut pas changer l'ordre des élement

dictionnaire : liste adressable
## opérateurs

| Opérateurs de comparaison | retournent un résultat booléen (`True` ou `False`) |
| ------------------------- | -------------------------------------------------- |
| `==`                      | égal                                               |
| `!=`                      | différent                                          |
| `>`                       |                                                    |
| `>`                       |                                                    |
| `>=`                      |                                                    |
| `<=`                      |                                                    |


| Opérateurs arithmétiques |                                                                                                       |
| ------------------------ | ----------------------------------------------------------------------------------------------------- |
| `%`                      | modulo ( reste d'une division ) <br>`5 % 2` retourne `1`<br>5 / 2, a un quotient de 2, et il reste 1. |
| `/`                      | division                                                                                              |
| `//`                     | division entière<br>par ex: si le résultat est 19.5, ça ne garde que 19                               |
| `+=`                     | Incrémentation : +=1<br>ajoute une valeur à une variable et assigne le résultat à la variable         |

| opérateurs logiques |                                                                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `and`               |                                                                                                                                 |
| `or`                |                                                                                                                                 |
| `not`               | negate an expression. When placed before a truthy value — a value that evaluates to `True` — it returns `False` and vice versa. |
Les opérateurs logiques fonctionnent bien sur des expressions qui renvoient une valeur unique

| Opérateurs bitwise |          | touche Mac  |
| ------------------ | -------- | ----------- |
| `&`                | et       |             |
| \|                 | ou       |             |
| ~                  | négation | `alt` + `N` |
Les opérateurs bitwise fonctionnent aussi sur les`Serie` (renvoient des valeurs pour chaque individus)



## Variables
Le scope détermine où la variable est accessible

- **définie en dehors d'une fonction** - scope global
  La variable est accessible n'importe où dans le code

- **définie dans une fonction** - scope local
  La variable n'est accessible que dans la fonction



## Déballage / unpacking
Le **déballage** (ou *unpacking* en anglais) d'un tuple en Python est une opération qui consiste à attribuer les éléments d'un tuple (ou d'une autre séquence, comme une liste) à des variables distinctes en une seule instruction.

### Exemple simple de déballage

un tuple avec trois éléments :

```python
t = (10, 20, 30)
```

on peux "déballer" ce tuple en trois variables distinctes :

```python
a, b, c = t
```

Après cette ligne, les variables auront les valeurs suivantes :
- `a = 10`
- `b = 20`
- `c = 30`

### Principe
Le déballage repose sur l'idée que le nombre de variables à gauche de l'opérateur d'affectation `=` doit correspondre au nombre d'éléments dans le tuple à droite.

### Déballage avec l'opérateur `*`

Il est également possible d'utiliser l'opérateur `*` pour capturer plusieurs éléments du tuple dans une seule variable, sous forme de liste.

Par exemple :

```python
t = (1, 2, 3, 4, 5)

# Déballage avec l'opérateur *
a, *b, c = t
```

Dans cet exemple :
- `a` recevra le premier élément : `1`
- `c` recevra le dernier élément : `5`
- `b` recevra tous les éléments du milieu sous forme de liste : `[2, 3, 4]`

### Utilisation courante
Le déballage est fréquemment utilisé pour :
- Extraire des éléments spécifiques d'une séquence (comme un tuple ou une liste).
- Échanger facilement les valeurs de deux variables :
  
  ```python
  x, y = y, x
  ```

- Passer des arguments à des fonctions lorsqu'une fonction attend plusieurs arguments.

### Exemple dans une fonction

Imaginons une fonction qui prend plusieurs arguments :

```python
def addition(a, b, c):
    return a + b + c
```

Tu peux appeler cette fonction en utilisant un tuple avec le déballage :

```python
t = (1, 2, 3)
resultat = addition(*t)
```

Ici, `*t` déballe le tuple `t` en trois arguments séparés : `1`, `2`, et `3`, qui sont ensuite passés à la fonction `addition`.

### Conclusion

Le déballage de tuples en Python est une fonctionnalité puissante qui permet de simplifier le code et d'améliorer sa lisibilité, tout en rendant certaines opérations, comme l'attribution de valeurs à plusieurs variables, beaucoup plus intuitives et concises.
## Classes
[[Programmation Orientée Objet]]
### built in classes

| classes | method      |                                                              |
| ------- | ----------- | ------------------------------------------------------------ |
| `str`   | `maketrans` | table de traduction, remplace des caractères dans une string |
|         |             |                                                              |
Chaque classe à ses propres méthodes (sortes de fonctions pour manipuler cette classe)

|          |                                 | appel                 |
| -------- | ------------------------------- | --------------------- |
| méthode  | spécifique à une classe         | `ma_classe.methode()` |
| fonction | applicable à toutes les classes | `fonction(ma_classe)` |

## Listes
```python
list = [on,peut,la, modifier, et mettre, différents, type, 1, 1.5, true ]
tuple = (on, ne, peut, pas, la, modifier)

dictionnaire = {  # met en relation un index et une valeu
				“prenom”: “Pierre”,
				“nom”: “malardier”
}                                     
```

[références : univ-paris-diderot.fr](https://python.sdv.univ-paris-diderot.fr/11_plus_sur_les_listes/)


#### Slicing  

| SLICING |          | par défaut         |
| ------- | -------- | ------------------ |
| début   | inclusif | 0 (début de liste) |
| fin     | exclusif | -1 (fin de liste)  |
| pas     |          | 1                  |
```python
ma_liste[début:fin:pas]

# Les 3 premiers éléments
ma_liste[:3]

# Tous les éléments à partir de l’indice 2
ma_liste[2:]

# Un élément sur deux
ma_liste[::2]

# Pas négatif, le début et la fin du slice sont inversés,ça inverse le tableau
ma_liste[::-1]

# tout la liste
ma_liste[:]
```


#### méthode sur liste

La méthode `.append()` ajoute un élément à la fin d'une liste
La méthode `.insert()` insère un objet dans une liste à un indice déterminé
L'instruction `del`supprime un élément d'une liste à un indice déterminé :
```pyhton
>>>a = [1, 2, 3]
    
>>>a.append(5)      
>>> a  
[1, 2, 3, 5]

>>> a.insert(2, -15)
>>> a  
[1, 2, -15, 3, 5]

>>> del a[1]
>>> a  
[1, -15, 3, 5]
```
  
`list.pop([i])`
Enlève de la liste l'élément situé à la position indiquée et le renvoie en valeur de retour. Si aucune position n'est spécifiée

 `a.pop() 
enlève et renvoie le dernier élément de la liste (les crochets autour du i dans la signature de la méthode indiquent que ce paramètre est facultatif et non que vous devez placer des crochets dans votre code ! Vous retrouverez cette notation fréquemment dans le Guide de Référence de la Bibliothèque Python).


## Compréhension de liste
Manière concise de créer des listes. Elle permet de générer une nouvelle liste en appliquant une expression à chaque élément d'un itérable.

Syntaxe  :  expression for itérateur in itérable
exemple :     2 * i        for    i           in    range(10)

| expression | 2*i       | `2 * i` est évaluée pour chaque valeur de `i`.                                 |
| ---------- | --------- | ------------------------------------------------------------------------------ |
| itérateur  | i         | `i` prend successivement chaque valeur de la séquence générée par `range(10)`. |
| itérable   | range(10) | génère une séquence de nombres de 0 à 9.                                       |
| résultat   |           | `[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]<br>                                       |


## Boucles for et while

L'exécution de for est plus long que celle de while
début
condition : oui ou non  
tant que la condition est vrai on exécute les instructions
```python
mot =”pierre”
```
crée la variable lettre :
```python
for lettre in mot 
```

Avec un for on crée une variable
crée la variable i :
```python
for i in 
```

Instructions if, if else, if elif else

Le code est lu de haut en bas.  
Si une condition est respectée, la boucle s’arrête.  
Sinon il continue

2 if à la suite, les 2 if seront parcourus



## Fonctions
Bloc de code réutililsable, évite les répétition de code 
Il faut la faire la plus générique possible parce qu’elle est destinée à être réutilisée
- built in (fournie de base avec python, intégrée au langage)
- définie par nos soins
### Fonctions built-in
 

| Fonctions built-in  |                                                                       |                                                                                                                                 |
| ------------------- | --------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `help(ma_fonction)` | affiche l'aide de la fonction, ses arguments etc...                   |                                                                                                                                 |
| `len()`             | retourne la longueur (c'est-à-dire le nombre d'éléments) d'un objet.  | fonction polyvalente qui fonctionne sur divers types d'objets en appelant la méthode spéciale `__len__` définie sur ces objets. |
| `print()`           |                                                                       |                                                                                                                                 |
| `int()`             | converti en entier                                                    |                                                                                                                                 |
| `ord()`             | renvoie le code ASCII du caractère passé en argument.                 |                                                                                                                                 |
| `chr()`             | renvoie le caractère ASCII correspondant au nombre passé en argument. |                                                                                                                                 |

| Méthodes     | <br>                                                                                                                          |                                                                                                                                               |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
|              |                                                                                                                               |                                                                                                                                               |
| `.find()`    | recherche la première occurrence d'une sous-chaîne spécifiée dans la chaîne si elle est trouvée, sinon elle retourne -1.      | - `start` : (optionnel) la position de début où commencer la recherche.<br>- `end` : (optionnel) la position de fin où terminer la recherche. |
| `.index()`   | similaire à `find()`, mais elle lève une exception `ValueError` si la sous-chaîne n'est pas trouvée, au lieu de retourner -1. | - `start` : (optionnel) la position de début où commencer la recherche.<br>- `end` : (optionnel) la position de fin où terminer la recherche. |
| `.isalpha()` | retourne `True` si tous les caractères de la string appelée sont des lettres                                                  |                                                                                                                                               |

| Module     | ensemble de fonctions et de méthodes                         |     |
| ---------- | ------------------------------------------------------------ | --- |
| [[random]] | Génèrer des valeurs aléatoire, manipuler des séquences, etc. |     |

### Définir une fonction

mot clé `def` 
nom de la fonction
parenthèses avec ou sans argument
deux point
A la ligne, une indentation et le code de la fonction :
```python
def ma_fonction():
	ici les instructions ou alors pass
```

### Argument
Pour faire son traitement, la fonction peut prendre des  arguments en entrée.
Ils sont utiles quand ils sont appelés a changer :  
sont des variables/paramètre/arguments qui permettent de modifier le résultat de la fonction

Sont séparés par une virgule 
```python
ma_fonction(arg_1, arg_2,...)
```

#### Argument par défaut
On peut spécifier la valeur par défaut d'un argument
Cette valeur par défaut sera prise en compte à l'appel de la fonction
```python
def ma_fonction(a, b, c=value):
    <code>
# On ne précise pas le troisième argument, il prendra donc la valeur par défaut
ma_fonction(1, 2)
```

exemple :
```python
etudiants = {}

def ajouterEtudiants():
	prenom = input(“Prenom : ”)
	nom = input(“nom: “)
	etudiant.update({“prenom”:prenom, “nom”:nom})
```
##### return
- donne la valeur à la fonction
- sert à stocker une donnée
- arrête la fonction
### Appel d'une fonction

Une fois la fonction définie, il faut l'appeler, sinon il ne se passe rien :
```python
nom_de_la_fonction()
```


## Fstring

- caractère `f` avant les guillemets d'ouverture
- insérer du code dans la string entre `{}`
	- instruction de mise en forme après `:`
	- Par exemple, un nombre suivi d'une lettre permet de spécifier une largeur

```python
print(f"chaine de caractère contenant entre accolades {du code}, par exemple une {variable}.)
```

```python
a = 1
b = 2
print(f"Les valeurs sont {a:10} et {b:10}")

>>> Les valeurs sont     1 et    2
```

| option /<br>paramètre de formatage | résultat                                                                                                                                   |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `:10`                              | affiche sur une largeur de 10 caractères<br>Il y a dans la chaîne produite un nombre de caractères fixé pour afficher la valeur entre { }. |
| `:>`                               | aligne à gauche                                                                                                                            |
| `:< `                              | aligne à droite                                                                                                                            |
| `:^`                               | aligne au centre                                                                                                                           |

 
## Strings

Other helpful string module features:

ascii_letters = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'

 ascii_lowercase = 'abcdefghijklmnopqrstuvwxyz'

ascii_uppercase = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'

digits = '0123456789'

hexdigits = '0123456789abcdefABCDEF'

octdigits = '01234567'

printable='0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~ \t\n\r\x0b\x0c'

punctuation = '!"#$%&\'()*+,-./:;<=>?@[\\]^_`{|}~'

whitespace = ' \t\n\r\x0b\x0c'

La fonction ord() renvoie l’unicode de la table ascii d’un caractère spécifié

La fonction chr() renvoie le caractère correspondant à l’unicode de la table ascii .

## Horloge

La méthode `strftime` (abréviation de "string format time") est une méthode du module datetime en Python qui permet de formater un objet datetime en une chaîne de caractères selon un format spécifié. Elle prend un format en tant qu'argument et renvoie une chaîne représentant la date et l'heure selon ce format

| ``%Y`` | Année sur quatre chiffres. |
| ------ | -------------------------- |
| ``%m`` | Mois (01 à 12)             |
| ``%d`` | Jour du mois (01 à 31)     |
| ``%H`` | Heure (00 à 23)            |
| ``%M`` | Minutes (00 à 59)          |
| ``%S`` | Secondes (00 à 59)         |


## JSON
Pour lire un fichier JSON, on utilise la fonction load du module json.

Il faudra au préalable ouvrir le fichier en mode lecture, par exemple avec l'instruction with :

import json

with open("/chemin/vers/le_fichier.json", "r") as f:

    data = json.load(f)

  

content_copy

On passe à la fonction load l'objet qui correspond au fichier ouvert, qui dans le cas ci-dessus est contenu dans la variable f.



## 𝗦𝗸𝗶𝗺𝗽𝘆
une librairie qui permet de remplacer avantageusement le .𝗱𝗲𝘀𝗰𝗿𝗶𝗯𝗲().  
Permet d'obtenir les statistiques les plus importantes, la part de valeurs manquantes, les distributions et quelques infos supplémentaires, groupées par type de variables.  
  
Beaucoup plus facile à lire que le .𝗱𝗲𝘀𝗰𝗿𝗶𝗯𝗲() traditionnel et facile à utiliser :  

```python
𝗳𝗿𝗼𝗺 𝘀𝗸𝗶𝗺𝗽𝘆 𝗶𝗺𝗽𝗼𝗿𝘁 𝘀𝗸𝗶𝗺  
𝘀𝗸𝗶𝗺(𝗱𝗳)
```

