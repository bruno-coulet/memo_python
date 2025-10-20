### intro

**design** **pattern** (_patron_ ou modèle de conception)
solution éprouvée et réutilisable à un problème qui se produit fréquemment

décrit la nature statique ou dynamique des classes et objets qui implémentent la solution

3 patterns adaptés à Python.

- pattern Constant **:** 
  très simple
  facilite la mise à jour des valeurs dans le code pour les développeurs.

- pattern Décorateur (« **Decorator** **»)** **:** 
  ce pattern de complexité modérée facilite la création de nombreuses fonctions qui accomplissent des choses similaires.

- **Le pattern Modèle-Vue-Contrôleur («** **Model-View-Controller** **»)** **:** 
  ce pattern constitue une architecture que vous pouvez utiliser pour votre application dans son ensemble, facilitant la fiabilité des interactions des utilisateurs avec votre système.

## design pattern Constant

Un nombre ou une chaîne fixe dans le code le rend compliqué à maintenir
Il vaut mieux déclarer des constantes en début de code autant que possible.

Le code appelle ces constantes et fonctionne toujours si l'on change leur valeur avant de lancer le programme.
Les constantes ne doivent pas être modifiée une fois le programme lancé (immutable)

Avantages :
- Les valeurs qui se répètent peuvent être définies une seule fois dans l’application.
    
- Les futurs développeurs pourront facilement comprendre la signification de la valeur.
    
- Les futurs développeurs pourront facilement modifier la valeur si les prérequis sont modifiés.

## design pattern Décorateur
**séparer la responsabilité** de la _partie qui change_ des parties qui ne changent pas

utilise des fonctions comme arguments d’autres fonctions
une sous fonction ajoute du code à la fonction passée en paramètre
cette sous fonction prend un nombre de paramètres dynamiques

résultat : la fonction exécute du code avant et après sa propre exécution

autrement dit : prend une fonction en entrée pour en donner une autre en sortie
#### Étape 1

Créer une **fonction décorateur** qui :
- attend une autre fonction en paramètre,
- et retourne une variation **décorée** de cette fonction en retour.

Le décorateur n’est qu’un **modificateur de fonction**. Il va la **transformer** pour rajouter des choses _avant_, et _après_.

#### Étape 2

Chaque changement fait dans le décorateur se répercute directement dans les fonctions décorées


#### Concretement
La syntaxe  `@decorate_function`  dit à l’interpréteur Python que cette fonction doit être décorée par la fonction décorateur  `decorate_function` 

Exemple :
```python
from time import time, sleep

# Cette fonction va générer le décorateur.
def calculate_time_spent(function):
    """calcule le temps que met une fonction à s'executer."""

    # paramètres dynamiques permet au décorateur de s'adapter à tout type de fonction !
    def wrapper(*args, **kwargs):
        """Décore la fonction avec un calcul du temps."""
        start = time()
        result = function()
        end = time()
        time_spent = end - start
        print(f"secondes passées: {time_spent:.2f}")
        return result

    return wrapper

  
  
# le @ nom_de_la_fonction assigne le décorateur à la fonction décorée
@calculate_time_spent
def calculate_the_trajectory():
    """Calcule la trajectoire du vaisseau."""
    print("Calcul en cours...")
    sleep(3)  # on met le programme en pause pendant 3 secondes !
    print("Calcul terminé !")

  

calculate_the_trajectory()
```

## pattern d’architecture MVC
**Modèle-Vue-Contrôleur**

système plus facile à :
- comprendre
- modifier 
- tester 
- réparer

une approche d’architecture de logiciel
divise les responsabilités du système en 3 parties distinctes :

| modèle                  | vue                                           | contrôleur                                                   |
| ----------------------- | --------------------------------------------- | ------------------------------------------------------------ |
| informations sur l’état | éléments qui interagissent avec l’utilisateur | s’assure que la séquence des étapes se déroule correctement. |
L’utilisateur interagit avec la vue, qui interagit à son tour avec le contrôleur

- **Modèle** **:** Le modèle contient les informations relatives à l’état du système. Ce sont les fonctionnalités brutes de l’application.
    
- **Vue** **:** La vue présente les informations du modèle à l’utilisateur. Elle sert d’interface visuelle et/ou sonore pour l’utilisateur.
    
- **Contrôleur** **:** Le contrôleur garantit que les commandes utilisateurs soient exécutées correctement, modifiant les objets du modèle appropriés, et mettant à jour l’application. C’est finalement les rouages de l’application, et c’est la couche qui apporte une interaction avec l’utilisateur.
![MVC](mvc.png)

### Modèle

Les **informations relatives à l’état** sont conservées dans les classes du modèle
éléments qui sont vus et manipulés

### Vue
tout les composantes du système qui assurent l’interface avec l’utilisateur

façon dont le modèle est présenté à l’utilisateur, et dont il **interagit** avec lui.
C’est l’élément qui est le plus susceptible de changer

### Contrôleur
sorte de colle entre le modèle et la vue
gère le flux de l'application
séquençage des interactions entre l’utilisateur et le système
apporte les modifications aux objets du modèle
en crée de nouveaux
supprime ceux dont on n’a plus besoin


## SOLID

Les designs plus propres sont plus faciles à comprendre, maintenir, modifier, et tester.

Si l’on suit les principes SOLID, on obtient un design plus propre.

Les principes SOLID sont :
    
    ○      Responsabilité unique (« single responsibility »).
    
    ○      Principe ouvert/fermé (« open/closed »).
    
    ○      Substitution de Liskov.
    
    ○      Ségrégation des interfaces (« interface segregation »).
    
    ○      Inversion des dépendances (« dependency inversion »).
    
### S : single responsability
Chaque classe ou fonction doit faire une seule chose, et la faire bien. Elle ne doit avoir qu’une seule raison de changer.

### O : open/closed
ouvrt à l'extension, fermé à la modification

### L :  substitution de Liskov
Les sous-classes doivent pouvoir faire tout ce que font leurs classes parentes. Si une ses sous-classes remplace une classe parente, cela ne doit pas casser le système

### I : interface segregation
responsabilité unique appliqué aux interface

### D : inversion des dépendances
Les classes parentes ne doivent pas avoir à changer lorsque l’une de leurs sous-classes est modifiée.