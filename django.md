Installer django
`pip install django`

Vérifier quelle version est installé
` python -m django --version`


créer un répertoire `mysite` dans le répertoire courant :
``django-admin startproject mysite

Aller dans le dossier `mysite` qu'on vient de créer :
`python manage.py runserver`

Avec le navigateur, aller sur localhost ou 127.0.0.1.8000



- Modifiez les modèles (dans `models.py`).
- Exécutez [`python manage.py makemigrations`](https://docs.djangoproject.com/fr/5.0/ref/django-admin/#django-admin-makemigrations) pour créer des migrations correspondant à ces changements.
- Exécutez [`python manage.py migrate`](https://docs.djangoproject.com/fr/5.0/ref/django-admin/#django-admin-migrate) pour appliquer ces modifications à la base de données

### Création d’un utilisateur administrateur[¶](https://docs.djangoproject.com/fr/5.0/intro/tutorial02/#creating-an-admin-user "Lien permanent vers ce titre")

Nous avons d’abord besoin de créer un utilisateur qui peut se connecter au site d’administration. Lancez la commande suivante :

$ python manage.py createsuperuser

