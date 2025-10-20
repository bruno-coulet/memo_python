

1. créer un fichier `.env`
   y mettre les constantes de connexion au format `clé=valeur`
   ```python
USERNAME=mon_identifiant
PASSWORD=mon_mot_de_passe
DOWNLOAD_DIR=C:\Users\Bruno\Downloads
URL=https://site.exemple.com

   ```
2. ajouter le fichier `.env` au `.gitignore`
3. Dans le script :

```python
import os
from dotenv import load_dotenv
load_dotenv()


USERNAME = os.getenv('USERNAME')
PASSWORD = os.getenv('PASSWORD')
DOWNLOAD_DIR = os.getenv('DOWNLOAD_DIR')

URL = os.getenv('URL')
```
