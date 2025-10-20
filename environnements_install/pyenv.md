
Pyenv est un outil puissant pour gérer plusieurs versions de Python sur un même système. Voici comment l'utiliser et ses avantages par rapport à conda env ou venv :


1. Installation d'une version de Python :
   ```bash
   pyenv install 3.11.5
   ```

2. Définir une version globale :
   ```bash
   pyenv global 3.11.5
   ```

3. Définir une version locale pour un projet :
   ```bash
   pyenv local 3.11.5
   ```

4. Lister les versions installées :
   ```bash
   pyenv versions
   ```

## Avantages de pyenv

1. Gestion fine des versions Python :
   - Permet d'installer et de basculer facilement entre différentes versions de Python[1][3].
   - Offre la possibilité de définir des versions spécifiques par projet[3].

2. Isolation des environnements :
   - Crée des environnements isolés pour chaque projet, évitant les conflits de dépendances[1].

3. Flexibilité :
   - Permet d'activer simultanément plusieurs versions de Python[3].
   - Facilite les tests sur différentes versions de Python sans changer la configuration globale[3].

4. Simplicité d'utilisation :
   - Commandes intuitives pour gérer les versions Python[5].

## Comparaison avec conda env et venv

- Par rapport à conda env :
  - Pyenv se concentre uniquement sur la gestion des versions Python, tandis que conda gère aussi les packages et les environnements[2].
  - Pyenv offre une plus grande flexibilité pour les versions Python spécifiques aux projets[1].

- Par rapport à venv :
  - Pyenv permet de gérer plusieurs versions de Python, alors que venv crée des environnements virtuels basés sur une seule version de Python.
  - Pyenv offre une meilleure isolation entre les projets et les versions Python[.

En résumé, pyenv est particulièrement utile pour les développeurs travaillant sur des projets nécessitant différentes versions de Python, offrant une gestion plus fine et flexible que conda env ou venv.
