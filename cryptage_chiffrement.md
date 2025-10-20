Selon le RGPD :
si on on doit garder les données personnelles sur les bases de données
(le mieux étant de les supprimer toutes les 24 heures)
il faut les crypter

clé publique sert à chiffrer
clé privé sert à déchiffrer

```python
from werkzeug.security import generate_password_hash
from werkzeug.security import check_password_hash
```

```python
mot_de_passe = "blabla"
mot_de_passe_hash = generate_password_hash(mot_de_passe)
```
Le hashage test la validité de quelque chose
la fonction check_password_hash verifie si