## Intro
https://flask.palletsprojects.com/en/2.3.x/quickstart/

C'est un micro-framework web écrit en Python. Il permet de concevoir une application web solide de manière professionnelle.
Inspiré de django et pylons, simplicité, modularité facilité
permet de créer des application et des [[API]], des prototypes, extensibles

Ensemble de modules qui permettent de développer plus rapidement en fournissant des fonctionnalités courantes.

Lorsque vous concevez une application web, vous avez toujours besoin de :

- gérer les requêtes HTTP
- un serveur web
- Afficher des pages web dynamiques
- gérer les cookies
- ...
  
Pour éviter de coder ces fonctionnalités à chaque fois, un framework web fournit ces fonctionnalités pour commencer un projet sur des bases solides.

Donne un cadre de travail minimal et très léger pour créer un projet rapidement.

Contrairement à [Django](https://www.djangoproject.com/ ), un autre framework web programmé en [[Python]], il ne met pas à disposition une interface d'administration ou un [[ORM]]. Il ne permet pas non plus de créer une structure de projet grâce à une commande. À l'inverse, il cherche à rester le plus minimal possible.

## Importation de Flask projet openclassroom
```bash
pip install flask

# Verifie l'installation
pip list

brew install sqlite

pip install flask_sqlalchemy
```

## Application de Flask
Une application Flask minimale :
```python

from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello_world():
    return "<p>Hello, World!</p>``

if __name__ == "__main__":
    app.run()
```


1. Importe la classe Flask.
   Une instance de cette classe sert d'application [[WSGI]]  (standard spécifiant comment un serveur Web peut interagir avec une application Python)

2. Crée l'instance de la classe. 
	Le premier argument est le nom du module ou du package de l'application.  
	`__name__` est un raccourci pratique qui convient dans la plupart des cas.
	Nécessaire pour que Flask sache où chercher les ressources, comme les modèles (templates) et les fichiers statiques.

3. Le décorateur `route()`  indique à Flask quelle URL déclenche la fonction.
   
4. La fonction retourne le message qu'on veut afficher dans le navigateur de l'utilisateur.
   Le type de contenu par défaut est HTML, donc le code HTML présent dans la chaîne sera interprété et rendu par le navigateur.




### Modèle MVT

Organisation en 3 dossiers :

1. Model 
Structure de la base de donnée
Le model de chaque objet est représenté par une classe stockée dans models.py, chaque classe hérite de la classe parent db.Model
Deux parties sont à distinguer dans un modèle :
- la structure de l'item dans la base de données,
- les attributs d'instance exposés.

2. Vue             - fonction qui renvoie une réponse à une requette HTTP
            décoré par @app.route. ou route est l'URL qui correspond à une vue
3. Template.   - reçoit et affiche des variables




## Template
c'est une structure qui permet d'utiliser des instruction python
```html
<p>
{{ permet de mettre dans le template html des variables python  }}
{% permet d'utiliser des instructions python %}
</p>
```

Par exemple, pour afficher une liste d'élèves :
```python
liste_eleves = [
	{'prenom':'jean', 'nom':'dupond', 'classe':'1a'},
	{'prenom':'luc', 'nom':'moulin', 'classe':'2a'},
	{'prenom':'serge', 'nom':'blanc', 'classe':'3b'}
]
```

1. On appel le template eleves.html avec @app.route
2. La fonction eleve (associée à la route' /eleves') est chargée de retourner le template eleves.html  :

```python
@app.route("/eleves")
def eleves():
	return render_template("eleves.html", eleves=liste_eleves)
```

3. Il faut donc un template **eleves.html** :

```html
<h1>Liste d'élèves</h1>
	<ul>
		{% for eleve in eleves :%}
			<li>{{ eleve['nom'] }} {{ eleve['prenom'] }}, {{ eleve['classe'] }}<li>
		{% endfor %}
	</ul>
```
	Il faut indiquer la fin de l'instruction avec endfor, endif, end...


On peut appeler les paramètres passés dans l'URL:
`https://nomdedomaine/?c=parametre_1`
```python
request.arg.get['c']
```
retourne 'parametre_1'
La méthode  ``.get`` permet de retourner  ``none`` plutôt qu'un erreur si le paramètre n'existe pas


### console interactive de Flask

Les sessions de SQLAlchemy permettent de gérer les transactions SQL, autrement dit **un ensemble de requêtes**. Si l'une d'elles échoue, l'ensemble de la transaction est annulée et aucune requête n'est communiquée à la base.

_Mac OS ou Linux_
```bash
FLASK_APP=run.py flask shell
```

_Windows_
```bash
set FLASK_APP=run.py
flask shell
```

- `db.session.add()` : Cette méthode permet d'ajouter un item à la base. En paramètres, vous passez l'instance de l'objet que vous voulez créer.
    
- `db.session.commit()` : Chaque création est ajoutée dans une session. Lorsque vous avez terminé d'ajouter des éléments, vous devez indiquer à SQLAlchemy de faire les requêtes dans la base pour finaliser l'opération.
    
- `Content.query.all()` : Cette méthode renvoie tous les items de la table Content. En réponse, nous voyons que nous avons bien un item.

### Rappel :
- Une base de données est un ensemble d’informations organisé. Il en existe plusieurs types. Pour communiquer avec, il faut utiliser le langage SQL en faisant des requêtes
    
- Flask intègre un **ORM** (Object Relational Mapping)
  Transforme des requêtes Python en requêtes SQL
    
- Une table d’une base de données est représentée en Python sous la forme d’un modèle
    
- Vous pouvez interagir avec votre base de données en ouvrant une console Flask et en utilisant l’ORM



## Formulaire
HTML
Balise ``form`` avec 2 attributs ``action`` et ``method`` :
```html
<form action ="" method="">

<input type="text">
<input type="radio">  même attribut name pour chaque élément bouton-radio, pour qu'ils soient lié
<select><option value=""></option><select>
<textarea name="" id="" rows="" col=""></textarea>
```

1. Attribut ``method``       ``GET`` ou ``POST``
Défini la façon d'envoyer les données au serveur.

Par défaut, il est de type ``GET`` et les données sont transmises via l'URL
``request.args`` pour récupérer les données/arguments et les traiter avec pyhton

Il y  a aussi le type ``POST``, les données sont transmises dans le corps de la requête
Par défaut,``POST`` n'est pas accepté par ``@app.route``
Il faut donc le rajouter en paramètre dans une liste :
```python
@app.route("/eleves", methods=["POST"])
```

avec le type ``POST`` les paramètres ne sont pas envoyé dans l'URL.
Du coup ``request.args`` ne fonctionne plus, il faut utiliser ``request.form`` à la place.

2. Attribut `action`
Défini à quelle page /route / URL les vs sont transmises.

Par défaut, il correspond à la route actuelle. 

Avec Flask il est recommander de ne pas mettre la route en dur, car elle peut être amenée à changer.
A la place, on utilise le nom de la fonction qui est associée à la route :
```html
action="{{ url_for('nom_de_la_fonction_voulue_qui_correspond_à_la_route) }}"
```



Ajouter l'attribut `required` sur les champs obligatoires.			    

Balise label, la valeur se son attribut ``for`` doit correspondre à celle de l'attribut ``id`` de la balise ``input`` :
```html
<input type="" name="" value="" id="blabla">
<label
<label for="blabla">
```
Bouton pour envoyer le formulaire:
```html
<input type="submit" value="Envoyer le formulaire"> 
```
on peut aussi utiliser la balise

```html
<button type="submit"></button>
```

Lorsqu'on envoie le formulaire, les paramètre sont déterminés par l'attribut name et sont affiché à la suite de l'URL avec leur valeurs


## Fichiers statiques, héritage et templates

https://www.youtube.com/watch?v=urp_b3bWcfE&list=PLV1TsfPiCx8PXHsHeJKvSSC8zfi4Kvcfs&index=4

1. Créer un dossier `static` avec dedans des dossiers :
	 - templates
	 - css/styles.css
	 - img/logo.png
	 - js, etc...

2. Dans les templates, on peut mettre :

```html
<head>
<!--  lien vers le fichier css  -->
<link rel="stylesheet"
	  href="{{ url_for ('static', filename='css/style.css') }}">
<!-- logo dans la navbar  -->
<img src="{{ url_for ('static', filename='img/logo.png') }}" alt="logo">
<!-- etc...>
</head>
```

3. Créer un template de base utilisable par les autres templates `base.html` :

avec une  balise `{% block nom_du_block %}`, en général `{% block content %}`
pour définir ce qui va changer d'une page à l'autre 
```html
<!-- fichier base.html -->
<!DOCTYPE html>
<html>
<head>...</head>
<header>...</header>

<div id="container">
	{% block content %}
	{% endblock %}
</div>

<footer>...</footer>
</html>
```

4.  Inclure le template de base dans `autre_fichier.html`
avec les balises `{% extends  "nom_du_template" %}` et `{% block nom_du_block %}`

```html
<!-- autre fichier html -->
<div id="container">
	{% extend "base.html" %}
	
	{% block content %}
	<!-- Ici le contenu html spécifique à cette page-->
	{% endblock %}
</div>
```
