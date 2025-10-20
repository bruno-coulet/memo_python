[[Python#Classes]]

## Méthode
fonction à l'intérieur d'une classe, elle lui  appartient, elle est lié à sa classe

syntaxe d'une méthode :
`mon_objet_ma_methode(option)`

### Dunders
contraction de double underscore
aussi appelées **méthodes magiques** ou **méthodes spéciales**.
commencent et se terminent par un double underscore pour éviter les conflits de noms avec d'autres attributs ou méthodes définis par l'utilisateur. 

Ces méthodes sont utilisées pour définir des comportements spécifiques dans certaines situations. 

#### Exemples de dunders :
`__init__`
Initialisation de l'objet
est appelée automatiquement lorsqu'un nouvel objet est créé à partir d'une classe

` __str__`
Conversion de l'objet en chaîne.

`__len__`
Retourne la longueur de l'objet.

``__getitem__``
accéde à un élément de l'objet en utilisant la notation d'index.

``__setitem__``
défini la valeur d'un élément de l'objet en utilisant la notation d'index.

``__delitem__``
supprime un élément de l'objet en utilisant la notation d'index.  
  
L'utilisation de ces méthodes spéciales permet aux objets de se comporter de manière prévisible dans certaines situations, en les rendant compatibles avec des opérations spécifiques telles que l'itération, la conversion en chaîne, etc.



### `__init__`  initialisateur
```python
def __init__(self, argument_2, argument_3):
```
Est appellée lorsqu'une nouvelle instance de classe est créée.
Définie les valeurs initiales des variables d'instance
Son premier argument est la nouvelle instance `self` (par convention)



## variables d'instance

`self.nom_de_la_variable`
```python
def __init__(self, argument_2, argument_3):
	self.variables_d_instance_1
	self.variables_d_instance_2
	self.variables_d_instance_3
```


## Attributs
variables associées à une classe d'objet:
`mon_objet.mon_attribut`

Il n'est pas suivi de parenthèses permettant de donner des arguments suplémentaires (contrairement à la méthode)
exemple :
`mon_ndarray.size` : affiche le nombre d'élément du tableau grâce à l'attribut "size".

## méthodes d'instance
`self`est le premier argument de chaque méthodes
`self.`avant chaque variables d'instance



## heritage

sert à ne pas se répéter

la classe fille récupère les attibuts et méthodes de la classe mère.  
une classe fille peut avoir plusieur mère