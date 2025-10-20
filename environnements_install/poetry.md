
Ouil de création et gestion d'[[Environnement virtuel Python]]


## Windows
```python
# creation de l environnement virtuel
python -m venv ~/.poetry-env
# activation
source ~/.poetry-env/scripts/activate
# installation de poetry dans l'env
python -m pip install poetry
# création de l'alias pour l'activation
alias poetry="/c/Users/coule/.poetry-env/Scripts/poetry"
# Ajout de l'alias au fichier de configuration du shell (bash)
echo 'alias poetry="/c/Users/coule/.poetry-env/Scripts/poetry"' >> ~/.bashrc

```
Il n'y a plus qu'à Utiliser Poetry depuis cet environnement
**Pour utiliser Poetry** :

```bash
poetry --version
poetry install
poetry add <package>
```
## Mac

## Création d'un environnement virtuel avec Poetry

1. Naviguez vers le répertoire du projet dans le Terminal.
2. Initialisez un nouveau projet Poetry :

```bash
poetry init
```

3. Répondez aux questions interactives pour configurer votre projet[
    
    2
    
    ](https://blog.stephane-robert.info/docs/developper/programmation/python/poetry/).
4. Pour créer l'environnement virtuel :

```bash
poetry install
```

Cette commande crée un environnement virtuel et installe les dépendances spécifiées dans le fichier `pyproject.toml`[

voir (https://www.jetbrains.com/help/pycharm/poetry.html).

## Utilisation de l'environnement

- Pour activer l'environnement :

```bash
poetry shell
```

- Pour exécuter une commande dans l'environnement sans l'activer :


```bash
poetry run python votre_script.py
```

- Pour ajouter de nouvelles dépendances :

```bash
poetry add nom_du_package
```

Poetry gère automatiquement les dépendances et les versions compatibles dans l'environnement virtuel[

voir aussi](https://blog.stephane-robert.info/docs/developper/programmation/python/poetry/).

