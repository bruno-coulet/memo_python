
L'extraction de données avec Python est possible à partir de multiples sources : fichiers locaux (PDF, Excel, CSV), sites web, API, et bases de données.
Grâce à ses bibliothèques robustes comme `pandas`, `requests`, `BeautifulSoup`, ou `PyPDF2`, Python offre un moyen puissant d'automatiser l'extraction et la manipulation de données.

### 1. depuis des fichiers CSV et Excel

#### CSV :
Le format CSV (Comma Separated Values)
utilisé pour stocker des données tabulaires.

- **Bibliothèque :** `pandas`
   ```python
   import pandas as pd

   # Lire un fichier CSV
   data = pd.read_csv('data.csv')

   # Afficher les premières lignes du fichier
   print(data.head())
   ```

#### Excel (.xlsx):
`pandas` associé à `openpyxl`.

- **Bibliothèque :** `pandas`, `openpyxl`
   ```python
   import pandas as pd

   # Lire un fichier Excel
   data = pd.read_excel('data.xlsx', engine='openpyxl')

   # Afficher les premières lignes
   print(data.head())
   ```

### 2. depuis des fichiers PDF

#### PyPDF2 :
Permet d’extraire du texte à partir de fichiers PDF.

- **Bibliothèque :** `PyPDF2`
   ```python
   from PyPDF2 import PdfReader

   reader = PdfReader('document.pdf')
   page = reader.pages[0]
   text = page.extract_text()

   print(text)
   ```

#### pdfplumber :
Utilisé pour extraire des données complexes, comme des tableaux, depuis des PDF.

- **Bibliothèque :** `pdfplumber`
- **Exemple :**
   ```python
   import pdfplumber

   with pdfplumber.open('document.pdf') as pdf:
       page = pdf.pages[0]
       text = page.extract_text()

   print(text)
   ```

#### Tabula :
Outil spécialisé dans l'extraction de tableaux à partir de fichiers PDF.

- **Bibliothèque :** `tabula-py`
   ```python
   import tabula

   # Extraire les tableaux du PDF
   tables = tabula.read_pdf("document.pdf", pages='all')

   # Afficher les tableaux
   for table in tables:
       print(table)
   ```

### 3. depuis des sites web (Web Scraping)

Pour extraire des données de pages web, Python propose plusieurs bibliothèques. L'extraction est souvent utilisée pour recueillir des données dynamiques ou statiques présentes dans le HTML.

#### BeautifulSoup :
Bibliothèque populaire pour extraire des données à partir de balises HTML.

- **Bibliothèque :** `beautifulsoup4`, `requests`
- **Exemple :**
   ```python
   import requests
   from bs4 import BeautifulSoup

   # Faire une requête à la page web
   url = 'http://example.com'
   response = requests.get(url)

   # Extraire et analyser le contenu HTML
   soup = BeautifulSoup(response.text, 'html.parser')

   # Extraire le titre de la page
   title = soup.title.text
   print(title)
   ```

#### Selenium :
Utilisé pour extraire des données de sites web dynamiques générés par JavaScript.

- **Bibliothèque :** `selenium`
- **Exemple :**
   ```python
   from selenium import webdriver

   # Ouvrir le navigateur
   driver = webdriver.Chrome()
   driver.get("http://example.com")

   # Extraire le titre de la page
   title = driver.title
   print(title)

   # Fermer le navigateur
   driver.quit()
   ```

### 4. **Extraction de données depuis des API**

Les API permettent d'extraire des données de manière structurée à partir de services web, souvent sous forme de JSON ou XML.

#### Requests :
Cette bibliothèque permet de faire des requêtes HTTP pour interagir avec des API.

- **Bibliothèque :** `requests`
- **Exemple :**
   ```python
   import requests

   # Faire une requête GET à l'API
   url = 'https://api.example.com/data'
   response = requests.get(url)

   # Extraire les données au format JSON
   data = response.json()
   print(data)
   ```

### 5. **Extraction de données depuis une base de données**

Python permet de se connecter à diverses bases de données (MySQL, PostgreSQL, SQLite) et d'en extraire des données.

#### SQLite :
SQLite est une base de données légère souvent utilisée pour des projets locaux.

- **Bibliothèque :** `sqlite3`
- **Exemple :**
   ```python
   import sqlite3

   # Connexion à la base de données
   conn = sqlite3.connect('database.db')
   cursor = conn.cursor()

   # Extraire les données d'une table
   cursor.execute("SELECT * FROM users")
   rows = cursor.fetchall()

   for row in rows:
       print(row)

   # Fermer la connexion
   conn.close()
   ```

#### MySQL :
Pour extraire des données depuis une base MySQL, on peut utiliser la bibliothèque `mysql-connector`.

- **Bibliothèque :** `mysql-connector-python`
- **Exemple :**
   ```python
   import mysql.connector

   # Connexion à la base de données
   conn = mysql.connector.connect(
       host="localhost",
       user="username",
       password="password",
       database="database_name"
   )

   cursor = conn.cursor()
   cursor.execute("SELECT * FROM table_name")
   rows = cursor.fetchall()

   for row in rows:
       print(row)

   conn.close()
   ```