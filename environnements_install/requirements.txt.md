  [[Environnement virtuel Python]]

 vérifie la version des paquets que vous avez installés, en exécutant :
 `pip freeze`


 liste des paquets Python dont l'installation est requise dans un environnement virtuel pour que l'application s'exécute correctement.
 Doit être ajouter au dépôt pour que les collaborateurs puissent installer l'`env`
 
 Par exemple ce fichier indique la version exacte à utiliser pour `matplotlib`  , et une plage de versions utilisables pour `numpy`  et `requests`  :
 
 ```python
matplotlib==3.2.2
numpy>1.12
requests>2.0,<3.0
```

Il existe deux méthodes pour créer le fichier`requirements.txt` :
### manuellement
1. créer un fichier `requirements.txt`
2. ajouter dedans les éléments nécessaires
### automatiquement
Cette commande met le contenu de `pip freeze`  dans le fichier `requirements.txt`  .
```shell
pip freeze > requirements.txt
```


Crée un fichier requirements.txt qui liste les bibliothèques et dépendances du projet :
`pip freeze > requirements.txt


Installer les paquets Python répertoriés dans le fichier requirements.txt :
`pip install -r requirements.txt`