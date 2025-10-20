
Pour désinstaller Python 3.12 sur  Mac :

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

5. Vous pouvez également vérifier s'il reste des fichiers liés à Python 3.12 dans votre dossier utilisateur et les supprimer manuellement si nécessaire.

Quelques points importants à noter :

- Assurez-vous de bien utiliser "3.12" dans les commandes, car c'est la version spécifique que vous souhaitez désinstaller.
- Soyez prudent lors de l'utilisation de ces commandes, car elles suppriment des fichiers de manière permanente.
- Si vous avez installé des packages Python avec pip, vous voudrez peut-être les désinstaller séparément avant de supprimer Python.
- Cette méthode ne désinstallera que la version que vous avez installée manuellement, pas la version système de Python qui vient avec macOS.

Après avoir exécuté ces commandes, Python 3.12 devrait être complètement désinstallé de votre Mac. N'oubliez pas de vider la corbeille après pour libérer l'espace disque.

Citations:
[1] https://www.youtube.com/watch?v=sKLs3okxFTQ
[2] https://www.xda-developers.com/how-uninstall-python-macos/
[3] https://www.partitionwizard.com/partitionmanager/uninstall-python.html
[4] https://gist.github.com/dlzi/c2cb7e39835cb2da868de47394cd4e83
[5] https://www.youtube.com/watch?v=1wGY-pr5KZ0
[6] https://www.reddit.com/r/learnpython/comments/15pr4uf/how_to_uninstall_old_version_of_python_from_mac/?tl=fr
[7] https://discuss.python.org/t/removing-older-versions-of-python-from-imac/39950
[8] https://stackoverflow.com/questions/72005302/completely-uninstall-python-3-on-mac