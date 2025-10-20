
## Mac

Vérifier les versions de Python installées sur Mac
```bash
python --version
python3 --version
```

vérifier l'emplacement de l'installation Python, utilisez :
```bash
which python
which python3

# si installé via homebrew
brew list python
```

Gérer les versions avec pyenv
```bash
brew install pyenv
# Liste toutes les versions de Python installées via pyenv
pyenv versions
# voir toutes les versions de Python disponibles à l'installation
pyenv install --list
```



```bash
# Afficher le contenu du PATH
echo $PATH

# Modifier le PATH (modifier le fichier ~/.zshrc)
nano ~/.zshrc
export PATH=$PATH:/chemin/vers/nouveau/dossier


```

### Désinstaller Python sur  Mac 
Cette méthode ne désinstallera que la version installée manuellement.
Pas la version système de Python qui vient avec macOS :

0. Désinstaller séparément  les packages Python installé avec pip avant de supprimer Python.

1. Exécutez la commande suivante avec le Terminal pour supprimer le framework Python 3.12 :

   ```
   sudo rm -rf /Library/Frameworks/Python.framework/Versions/3.12
   ```

2. Supprimez ensuite le dossier d'application Python 3.12 :

   ```
   sudo rm -rf "/Applications/Python 3.12"
   ```

4. Enfin, supprimez les liens symboliques dans /usr/local/bin qui pointent vers cette version de Python :

   ```
   sudo find /usr/local/bin -lname '../../../Library/Frameworks/Python.framework/Versions/3.12/*' -delete
   ```

5. Vérifier s'il reste des fichiers liés à Python 3.12 dans le dossier utilisateur et les supprimer manuellement si nécessaire.


- Ces commandes suppriment des fichiers de manière permanente.

- vider la corbeille après pour libérer l'espace disque.


## Windows


1. Localiser l'interpréteur Python

Pour trouver l'emplacement de l'interpréteur Python dans un terminal Bash (affiche le chemin complet vers l'exécutable Python):

```bash
where python
```


2. Configuration des variables d'environnement

Pour configurer le chemin vers l'interpréteur Python dans les variables d'environnement système :

	1. Panneau de configuration
	2. Système
	3. Paramètres système avancés
	4. Variables d'environnement
	5. section Variables système, sélectionnez Path et cliquez sur Modifier
	6. Ajoutez le.s chemin.s 


## Désinstallation de Python

Pour désinstaller une version de Python :

1. Paramètres Windows
2. Applications
3. Applications et fonctionnalités
4. Recherchez "Python" dans la liste des applications installées
5. Sélectionnez la version de Python que vous souhaitez supprimer
6. Cliquez sur Désinstaller et suivez les instructions

Il est recommandé de désinstaller toutes les versions de Python que vous n'utilisez plus pour éviter les conflits potentiels entre différentes installations.

