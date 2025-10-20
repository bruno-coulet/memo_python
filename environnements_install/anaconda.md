anaconda.com/download

- Environnement de développement multiplateforme intégrant :
	  - un interpréteur python
	  - l'IDE Spyder
	  - les [[Notebook Jupyter]]

- distribution python libre qui intègre un grand nombre de packages
	gestionnaire de package conda
	
- entreprise de développement et d'environnement d'environnement

- système d'environnement et un répertoire de package orienté data

Anaconda est donc un système de gestion d'environnements de travail comme virtual-env [[Environnement virtuel Python]]

export d'environnement de travail sous forme de fichier  .yml qui contient :
- la version de python
- les packages et leurs dépendances

Invite de commande Anaconda : Anaconda Prompt
`(base)` est l'environnement racine avec tout les packages installés avec anaconda ( à l'installation et depuis)

| Action                                                     | Commandes                                    |
| ---------------------------------------------------------- | -------------------------------------------- |
| Vérifier l'installation de conda                           | `conda info`                                 |
| mettre a jour conda                                        | `conda update conda`                         |
| liste des package de l'environnement                       | `conda list`                                 |
| Installer un package depuis le répertoire Anaconda         | `conda install mon_package`                  |
| mettre a jour un package                                   | `conda update mon_package`                   |
| rechercher un pakage                                       | `conda search mon_package`                   |
| Installer un package depuis PyPi                           | `pip install mon_package`                    |
| Installer un package moins distribué<br>depuis conda-forge | `conda install --chanel conda-forge package` |

| Action                                               | Commandes                                                                                                                          |
| ---------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Vérifier les environnement installés                 | `conda info --envs`                                                                                                                |
| Créer et activer un env                              | `conda create --name mon_env`<br>activer sous Windows :<br>`activate mon_env`<br>activer sous Linux :<br>`source activate mon_env` |
| Cloner un env existant                               | `conda create --name mon_clone --clone mon_env_original`                                                                           |
|                                                      |                                                                                                                                    |
| Répliquer un env sans spécifier les versions et l'OS | `conda env export > environment.yml`                                                                                               |
| Charger l'env                                        | `conda env create -f environment.yml`                                                                                              |
| Répliquer un env précis (versions et OS inclus)      | `conda list -e > spec-file.txt`                                                                                                    |
| Cherger l'env sur une machine qui à le même OS       | `conda create --name MyEnvironment --file spec-file.txt`                                                                           |
