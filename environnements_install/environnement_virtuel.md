[[requirements.txt]]
[[Anaconda]]
[[pip - PyPi]]
[[Poetry]]
[[Pyenv]]
## Intro

Pour savoir où python est installé :``which python`` ou `where python`

On crée un environnement virtuel (appelé `env` ou `venv` par convention)
généralement à la racine du projet
avec un script ([[Bash Scripting]]) via :
- `uv`
- `venv`
- `virtualenv`(plus vieux)
- `Anaconda`
- `Poetry`


Cet environnement virtuel est isolé du système global et des  paquets Pythons globaux.

Est un ensemble de répertoires contenant une copie isolée des fichiers exécutables Python et une copie de la bibliothèque `pip`.

Les packages Python que l'on installe à l'intérieur de cet environnement ne seront accessibles qu'à cet environnement virtuel spécifique.
Toutes les commandes `python`, `pip`, etc. exécutées sont liées à l'environnement virtuel.

Cela est utile pour isoler les dépendances des différents projets Python.


Il y a plusieurs méthodes possibles pour créer un environnement virtuel :


1. `uv`

2. **`venv`**  :    à partir de Python 3.3 
         si on souhaite utiliser un outil intégré sans installation supplémentaire.

3. **`virtualenv`** : si Python antérieure à 3.3 (plus vieux)
              si besoin de fonctionnalités supplémentaires.



## méthode 1 : `uv`

Installation de `uv`
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv --version
```

Création d’un projet Python avec son environnement isolé :
```bash
# 1. Créer un projet + environnement
uv init nom_du_projet
# 2. Se déplacer dans le dossier
cd nom_du_projet
# 3. Installer des dépendances
uv add pandas numpy matplotlib scikit-learn
# 4. Synchroniser l’environnement avec le fichier pyproject.toml
uv sync
```

## ⚡ Faut-il activer l'environnement ?

Avec ``uv``, il n’est **pas toujours nécessaire d’activer l’environnement** manuellement.  

#### 🔹 1. Sans activation (méthode recommandée)
Exécuter directement les scripts avec `uv run` :

```bash
uv run python script.py
uv run jupyter notebook
uv run pytest
```
- L’environnement est utilisé automatiquement par uv.
- Plus propre et sûr : pas à se demander quel venv est actif.
#### 🔹 2. Activation classique (optionnelle)
Activer l’environnement comme avec `venv` ou `pipenv` 

```bash
# Linux / macOS
source .venv/bin/activate

# Windows (PowerShell)
source .venv\Scripts\activate
```
- Tous les python, pip et autres outils pointent vers l'environnement.
- Un shell “prêt à l’emploi” pour taper plusieurs commandes.

#### 🔹 3. Activation via uv activate
```bash
cd chemin/vers/nom_du_projet
uv activate nom_du_projet
```
Optionnelle, utile si tu veux rester dans un shell où .venv est actif.

En pratique, beaucoup de devs préfèrent soit activer .venv directement, soit utiliser uv run.

✅ Conclusion :
- Activation manuelle : facultative, pour travailler comme avec un venv classique.
- uv run : suffit pour tout exécuter, plus sûr et reproductible.


### Activation de l’environnement
```bash
# Linux / macOS
source .venv/bin/activate

# Windows (PowerShell)
.venv\Scripts\activate

# Ou directement avec uv
uv activate nom_du_projet
```
ℹ️ L’environnement est stocké dans .venv/ au sein du projet → simple, reproductible, portable.

❌ Mauvaise pratique (à éviter)
```bash
# Créer un venv global "quelque part"
uv venv ~/uv_env
source uv_env/bin/activate

# Installer les dépendances "en vrac"
uv pip install pandas numpy matplotlib scikit-learn
```
⚠️ Inconvénients :
- difficile de reproduire l’environnement ailleurs
- pas de pyproject.toml ni de gestion centralisée des dépendances
- risque de multiplier les venvs "orphelins"

## Commandes courantes `uv`

| Commande                | Description                                                     |
| ----------------------- | --------------------------------------------------------------- |
| `uv --version`          | Vérifie la version installée                                    |
| `uv init nom_projet`    | Crée un nouveau projet + venv + `pyproject.toml`                |
| `uv add package`        | Installe un paquet **et** l’ajoute au `pyproject.toml`          |
| `uv remove package`     | supprime un paquet et met à jour la config                      |
| `uv sync`               | Synchronise l’environnement selon `pyproject.toml` et `uv.lock` |
| `uv lock`               | génère/actualise le fichier `uv.lock` pour figer les versions.  |
| `uv run script.py`      | Exécute un script dans l’environnement sans activer `.venv`     |
| `uv pip list`           | Liste les paquets installés (comme `pip list`)                  |
| `uv pip show package`   | Affiche les infos sur un paquet                                 |
| `uv venv path/vers/env` | Crée un venv manuel (⚠️ à éviter si projet)                     |
| `uv activate`           | Active l’environnement d’un projet (`.venv`)                    |

On peux combiner **`uv run`** avec n’importe quelle commande Python :  

```bash
uv run python script.py
uv run jupyter notebook
uv run pytest
```


# Après avoir quitter l'environnement virtuel ou le terminal

cd chemin/vers/nom_du_projet

  

uv activate nom_du_projet

# ou

source .venv/bin/activate

# ou sous Windows

source .venv/Scripts/activate

## méthode 2 : `venv` 
`venv`=  virtual environement
`venv` est un module standard intégré à  [[Python]] à partir de la version 3.3.
Utilisé pour créer des environnements virtuels

```bash
python -m venv nom_de_l_environement_virtuel
# Par convention on appel l'environnement virtuel 'env'
python -m venv env
```
  
- `python`    :    Lance Python.
- `-m`  :     Exécute un module intégré de Python
- ` venv`  :    Sélectionne le  module `venv`
- `env`        :   Nomme l'environnement virtuel créé.

##### Etape suplémentaire avec Powershell
ajouter en mode administrateur :
```powershell
Set-ExecutionPolicy RemoteSigned
```
## Méthode 3 : `virtualenv`

Initialise l'environnement virtuel
```bash
pip install virtualenv

virtualenv env -p python3
```

Active l'environnement virtuel sur Unix (linux ou mac)
```bash
source env/bin/activate
```
Active l'environnement virtuel sur Windows
```bash
source env/Scripts/activate
```


## Activer l'environnement
1. Unix / Linux / Mac
```bash
source nom_de_l_environnement_virtuel/bin/activate
```

2. WINDOWS
```bash
source nom_de_l_environnement_virtuel/Scripts/activate
```

Exécute le script d'activation de l'environnement.

Sans cette commande, l'environnement virtuel serait créé mais non activé, il faudrait activer l'environnement virtuel séparément à chaque fois qu'on' travaille dans cet environnement. En utilisant `source`, vous pouvez automatiser cette étape dans votre script.


## `pip freeze` 

Génére une liste des packages installés avec leur versions : `package==version`
Directement utilisable pour un fichier `requirements.txt` :

```python
pip freeze > requirements.txt
```

## `pip list`

Lister les packages installés, avec quelques informations supplémentaires.
Tableau avec deux colonnes : le nom du package et sa version.
Parfois, des colonnes supplémentaires comme `Location` ou `Installer` peuvent être affichées.



## Désactiver l'environnement virtuel

Pour travailler sur un projet différent, il faut désactiver l'environnement virtuel  avec la commande suivante depuis n'importe quel répertoire :

```bash
deactivate
```

## Changer d'environnement virtuel

Pas besoin de désactiver un environnement virtuel avant d'en activer un autre.
Le fait d'activer un nouvel environnement désactive l'ancien :

1. aller dans le répertoire voulu
2. vérifier la présence d'un répertoire `env`
   ou en créer un avec `python -m venv env`
3. activer l' `env`

```shell
cd repertoire_voulu
ls
fichier_1.py fichier_2.py env
source env/bin/activate
```


## Supprimer l'environnement virtuel
```bash
# Supprimer l'ancien environnement virtuel s'il existe
rm -rf /chemin/vers/l\'environnment/virtuel/env/
# si on est dans le bon répertoire
rm -r env/
```
   
<font color="orange">Attention</font> si l'`env`est encore activé quand on le suprime :
Le `env`qui est ajouté à l'invite de commande peut rester en place.
Si cela se produit, tapez `deactivate`

- **`-r` ou `--recursive`**
    supprime les répertoires et leur contenu de manière récursive.
    
- **`-f` ou `--force`**
    supprime les fichiers sans demander de confirmation, même ceux en mode lecture seule. sans afficher de message d'erreur si les fichiers n'existent pas.

## Ajouter l' `env` au `.gitignore`

En général, le répertoire de l'environnement virtuel ne doit pas être inclus dans le dépôt Git d'un projet.
Il faut donc ajouter son répertoire au fichier `.gitignore` :

```shell
# Initialiser le dépôt git si besoin
git init
# crée le fichier .gitignore
touch .gitignore
# ouvre le fichier .gitignore avec vscode (ou autre)
code .gitgonre
# Ajouter env/ ou le nom_de_l'environnement/

# Verifier que le dosier de l'env est ignoré, il n'est pas dans la liste des fichiers non suivi (untracked)
git status
```



## Installation des paquet via `requirements.txt`

```bash
pip install -r requirements.txt
```

Installe les dépendances définies dans le fichier `requirements.txt` dans l'environnement virtuel activé.





