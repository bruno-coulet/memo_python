1. modules Python intégrés dans la bibliothèque standard

2. paquets Python
  Ensemble d'un ou plusieurs modules effectuant des tâches courantes
  Regroupés par des développeurs Python.
  Sont installés via le **Python Package Index**   : [PyPi](https://pypi.org/) 

## PyPi : Python Package Index
dépôt officiel des bibliothèques et modules Python. Il agit comme une base de données centralisée où les développeurs publient leurs packages pour les rendre accessibles à d'autres utilisateurs via `pip`
## pip : Pip Installs Packages

gestionnaire de paquets pour Python qui permet d'installer, de désinstaller et de gérer des bibliothèques et des dépendances disponibles dans l'écosystème Python.

   `pip`  utilise **PyPi** comme source par défaut pour ses paquets.
   installe, désinstalle et met à jour des paquets Python (et bien plus encore)

```shell
# Vérifier si python est installé, et sa version
python --version
# Vérifier si pip est installé
pip --version
```

```shell
# Alternative si pip est installé mais pas reconnu
python3 -m pip --version
```

| Commande                               | Effet                                                                                                                                                                                                         |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `pip install nom_du_paquet`            | installe la dernière version du paquet                                                                                                                                                                        |
| `python3 -m pip install nom_du_paquet` | Alternative pour installer le paquet                                                                                                                                                                          |
| `pip install nom_du_paquet==2.1.0`     | installe la version 2.1.0 du paquet                                                                                                                                                                           |
| `pip uninstall <package>`              | Désinstalle le paquet                                                                                                                                                                                         |
| `pip install requests~=2.2`            | installe la version la plus élevée disponible au-dessus de `2.2`  du paquet `request`, mais pas `3.0`  ni  ultérieures                                                                                        |
| `pip install requests~=2.1.0`          | installe la version la plus élevée disponible au-dessus de `2.1.0`  , mais pas la version `2.2.0`  ni ultérieures.                                                                                            |
| `pip install "requests>2.4.0,<2.6.0"`  | installe la version la plus élevée disponible supérieure à `2.4.0`  , mais inférieure à `2.6.0`<br><br>Pour spécifier un intervalle de versions :<br>- mettre entre guillemets<br>- séparer par des virgules. |
| `pip list`                             | répertorie tous les paquets installés (et leurs dépendances) dans un format intelligible                                                                                                                      |
| `pip freeze`                           | répertorie les paquets installés (pas leurs dépendances) dans un format adapté au stockage dans un fichier (souvent appelé fichier [[requirements.txt]] )                                                     |
| `pip show <package(s)>`                | montre des informations utiles sur un ou plusieurs paquets installés                                                                                                                                          |
| `pip show paquet1 paquet2`             | informations sur plusieurs paquets<br>(séparer les noms des paquets par des espaces)                                                                                                                          |
## Importez des paquets et modules Python

Utiliser un module Python de la bibliothèque standard  :

```python
# importe un module
import nom_du_module
# n'importe qu'une fonction du module
from nom_du_module import fonction_du_module
# importe tout le contenu d'un paquet 
from nom_du_module import *
```
<font color="orange">import * est pratique dans le shell python, mais c'est une mauvaise pratique dans le code d'une application</font>
Cela permet de ne pas écrire nom_du_module. en préfixe à chaque fois qu'on appelle une de ses fonction :

```python
from numpy import *
ceil(2,1)
ceil(1.2)
floor(1.2)
```
Equivaut à :
```python
import numpy
numpy.ceil(1.2)
numpy.ceil(1.933)
numpy.floor(1.2)
```

### Création d'alias de paquets

Possible d'importer un paquet avec un alias
Il faut alors utiliser l'alias en prefixe quand on appel une des fonctions du paquet.
```python
import nom_du_paquet as alias

alias.nom_de_la_fonction()
```

| Module |           |                                      |
| ------ | --------- | ------------------------------------ |
| os     | .getcwd() | affiche le current working directory |
