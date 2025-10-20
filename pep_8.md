Python Enhancement Proposal_ (proposition d'amélioration de Python)

[Les PEP](https://www.python.org/dev/peps/pep-0001/) sont des documents de conception pour la communauté Python. Elles décrivent des nouvelles fonctionnalités pour Python, ses processus ou son environnement

**PEP 257** 
document dédié aux conventions des chaînes de documentation.

[**PEP 8** ](https://peps.python.org/pep-0008/)  [texte intégral de la PEP 8](https://www.python.org/dev/peps/pep-0008/)
**guide de style** pour python, liste de pratiques suggérées pour les développeurs Python

## Nommage des éléments
Section de la PEP 8 sur les [conventions de nommage](https://www.python.org/dev/peps/pep-0008/#naming-conventions).
### variables
en `snake_case` :
en minuscules
avec des underscores

		`fuel_level = 100`


### variables constantes
en majuscules, avec des _underscores_

		`DAYS_PER_WEEK = 7

### classes
`CapitalizedCase`
majuscule au début de chaque mot
sans ponctuation

		`class JukeBox:`
		
Instance d’une classe en minuscules avec des tirets bas, par exemple_ _:  `my_request`_
### Modules
en minuscules, en évitant au maximum l’utilisation des _underscores_ :
    
```
import os
import sys
import shutil 
import pathlib
```


éviter les abréviations

## Commentaires
section sur les [commentaires](https://www.python.org/dev/peps/pep-0008/#comments) de la PEP 8.

phrases complètes en anglais
Mettre les commentaires à jour lorsque le code change.
Éviter les commentaires sur la même ligne que le code.
Un seul espace entre le symbole dièse et le texte (pour différencier du code qui a été commenté).
Utilisez le même niveau d’indentation que la ligne de code qui suit, pour une bonne lisibilité

## Docstrings
[PEP 257 -- Docstring Conventions](https://www.python.org/dev/peps/pep-0257/).
commentaires spéciaux écrits au tout début d’une fonction, d’une classe ou d’un module, et utilisés pour la **documentation**.

permet de décrire le code.
permettent aux outils automatisés d’accéder au texte, par exemple pour générer une documentation en ligne de votre code

apportent une **couche de documentation** à votre code, elles seront toujours un **gain qualitatif et une aide** dans votre projet

<font color='orange'>ne doit pas décrire le fonctionnement interne de sa fonction ou méthode, mais seulement son retour.</font> Il ne s’agit pas d’expliquer le code, mais **d’expliquer son usage**.
```python
def search_film(name):
    """Cherche un film selon un nom donné.
 
    Retourne un objet film si un film a été trouvé, sinon None.
    """
    ```
    
encore mieux :

```python
def search_film(name):
    """Cherche un film selon un nom donné.
 
    Attrs:
    - name (str): le nom utilisé pour la recherche.
 
    Returns:
    - un objet `film` si un film a été trouvé, ou None.
    """
    # ...
```


Les docstrings en début de fonction ou de classe sont spéciales, et on peut y accéder en utilisant l’attribut  `__doc__`  :

```
print(multiply.__doc__)
```


## indentation
 soit des espaces, soit des tabulations, mais pas un mélange des deux. 
 il est **recommandé d’utiliser 4** **espaces**

## espaces
[espaces dans les expressions et instructions](https://www.python.org/dev/peps/pep-0008/#whitespace-in-expressions-and-statements) 
 
 **un seul espace** autour des opérateurs d’affectation

 **jamais d’espaces** tout de suite à **l’intérieur de parenthèses ou de crochets**

**pas de blanc** entre une fonction, comme  `print()`  , et ses arguments

**un espace** entre  `if`  et **toute parenthèse**. La même règle s’applique à  `for`

## Saut de ligne
 [sauts de lignes](https://www.python.org/dev/peps/pep-0008/#blank-lines)
- deux lignes :
	- Avant une définition de classe  `class MyClass`  
	- une définition de fonction  `def my_function(...):`  
    
- une seule ligne :
	- Avant une définition de méthode au sein d’une classe

## Longueur de ligne

**limiter les lignes de code à 79** **caractères**

Si une fonction a trop de paramètres pour tenir sur 79 caractères :
Aligner les paramètres sur la verticale
```python
	def function_with_a_long_name(parameter_number_1,
								  parameter_number_2,
								  parameter_number_3):
    my_function(parameter_number_1)
    return parameter_number_2
```
Ou
```python
# Un paramètre par ligne, et la parenthèse au même niveau d’indentation que la fonction
def function_with_a_rather_long_name(
    parameter_number_1,
    parameter_number_2,
    Parameter_number_3
):
    my_function(parameter_number_1)
    return parameter_number_2
```

Si une chaîne de caractère est trop longue :
découper la chaîne en plusieurs petites chaînes
les insérez à l’intérieur de parenthèse séparées seulement d’un **saut de ligne**.

Lors de l'exécution du code, elles vont se « _**recoller**_ » pour n’en former qu’une grande.
```
super_long_password = (
    "erfzfefrzvterbytnrezrtvbytyruetrgtrth"
    "zeergvzreafz'((-'eg'((yhvgbrz'trvytrh"
    "zerbetrtzbrtyezegbyebzrtbrebrtberbtrg"
    "zevrebtniukoy;i;yu,yt,trntehtrgegretr"
)
```



## organisation du code
PEP 8 sur les [imports](https://www.python.org/dev/peps/pep-0008/#imports)

1. Les commentaires qui concernent la totalité du fichier vont en haut.
2. Les imports suivent cet ordre :
    1. Modules de la bibliothèque standard, par exemple  `import random`  .    
    2. Modules de bibliothèques tierces, par exemple  `import sklearn`  .    
    3. Modules locaux, par exemple  `import mymodule`  .    
3. Les constantes, par exemple  `MY_CONSTANT = 77`  .
4. Tout autre code.
    

## return

- Soit toutes les instructions  `return`  retournent une valeur, soit aucune ne le fait.
    
- Tous les types de retours doivent être les mêmes (sauf s’il y a une très bonne raison de faire autrement !).
    
- Utilisez  `return None`  plutôt qu’un  `return`  nu.

## chaine de caractère

utiliser les fonctions `str.startswith` et  `str.endsswith`
ou la bibliothèque d’expressions régulières de Python : [re](https://docs.python.org/3/library/re.html)


## Simplifier les exceptions
utiliser les **blocs try-except**.
- Les blocs try doivent être placés de façon à couvrir le moins de code possible.
- Les clauses except doivent toujours attraper un type spécifique d’exception.

## Linter et formateur

Un des linters les plus connus est [Flake8](https://flake8.pycqa.org/en/latest/) ( bibliothèque Python à installer )
Il permet notamment à votre éditeur de code (il faut le paramétrer) de trouver les erreurs de convention PEP 8, reste  à les corriger ou pas.

[[Formateur black]]
Le formateur black formate le fichier conformément à la PEP8
```python
pip install flake8
flake8 nom_du_fichier.py

pip install black
black nom_du_fichier.py
```
