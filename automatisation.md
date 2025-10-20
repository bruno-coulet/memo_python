L’automatisation des tâches avec Python est très polyvalente, que ce soit pour gérer des fichiers, interagir avec des pages web, manipuler des bases de données ou encore envoyer des emails. Python offre un large éventail de bibliothèques adaptées à différents besoins, permettant ainsi de créer des workflows automatisés efficaces.

lancer des commande en python
os
 

### 1. tâches courantes sur le système
   Python permet d’automatiser des tâches comme la gestion de fichiers, l’exécution de scripts, et la manipulation de dossiers.
   
   - **Bibliothèques** :
     - `os` et `shutil` pour gérer les fichiers et les répertoires.
     - `subprocess` pour exécuter des commandes système.
     - **Exemple** :
       ```python
       import os
       import shutil

       # Déplacer un fichier
       shutil.move('source.txt', 'destination.txt')
       
       # Lister les fichiers dans un répertoire
       print(os.listdir('/path/to/directory'))
       ```

### 2. tâches web (web scraping)
   L’automatisation des tâches sur le web, comme l’extraction d’informations depuis des pages web ou l’interaction avec des sites web, est facilitée par Python.

   - **Bibliothèques** :
     - **BeautifulSoup** pour extraire des données HTML.
     - **Selenium** pour automatiser les navigateurs web.
     - **Requests** pour envoyer des requêtes HTTP.
     - **Exemple** :
       ```python
       import requests
       from bs4 import BeautifulSoup

       url = 'http://example.com'
       response = requests.get(url)
       soup = BeautifulSoup(response.text, 'html.parser')

       # Extraire et afficher le titre de la page
       print(soup.title.text)
       ```

### 3. tâches liées aux fichiers Excel et PDF
   Python est très efficace pour automatiser la gestion des fichiers Excel ou PDF.

   - **Bibliothèques** :
     - **openpyxl** pour lire et écrire des fichiers Excel.
     - **PyPDF2** ou **pdfplumber** pour extraire du texte depuis des PDF.
     - **Exemple (PDF)** :
       ```python
       from PyPDF2 import PdfReader

       reader = PdfReader('file.pdf')
       page = reader.pages[0]
       print(page.extract_text())
       ```

### 4. rapports et génération de documents
   Générer des rapports, des documents Word ou PDF peut être automatisé grâce à Python.
   
   - **Bibliothèques** :
     - **python-docx** pour créer ou manipuler des fichiers Word.
     - **pdfkit** ou **reportlab** pour générer des fichiers PDF.
     - **Exemple (Word)** :
       ```python
       from docx import Document

       doc = Document()
       doc.add_heading('Rapport', 0)
       doc.add_paragraph('Voici un paragraphe ajouté automatiquement.')
       doc.save('report.docx')
       ```

### 5. emails
   Python permet d’automatiser l’envoi d’emails, par exemple pour envoyer des rapports ou des alertes.

   - **Bibliothèques** :
     - **smtplib** pour envoyer des emails via SMTP.
     - **email** pour composer des messages.
     - **Exemple** :
       ```python
       import smtplib
       from email.mime.text import MIMEText

       msg = MIMEText('Ceci est un email automatique.')
       msg['Subject'] = 'Notification'
       msg['From'] = 'your_email@example.com'
       msg['To'] = 'recipient@example.com'

       with smtplib.SMTP('smtp.example.com') as server:
           server.login('your_email@example.com', 'password')
           server.send_message(msg)
       ```

### 6. processus métiers
   Python peut interagir avec des API pour automatiser des flux de travail complexes, comme la gestion des stocks, le suivi des tâches ou l’envoi de notifications.

   - **Bibliothèques** :
     - **Requests** pour interagir avec les API REST.
     - **Exemple** :
       ```python
       import requests

       response = requests.get('https://api.example.com/data')
       print(response.json())
       ```

### 7. gestion des bases de données
   Python permet d’automatiser l’interaction avec les bases de données pour insérer, mettre à jour ou extraire des données.

   - **Bibliothèques** :
     - **sqlite3** pour les bases de données SQLite.
     - **SQLAlchemy** pour un ORM plus général.
     - **Exemple** :
       ```python
       import sqlite3

       conn = sqlite3.connect('database.db')
       cursor = conn.cursor()
       cursor.execute('SELECT * FROM users')
       print(cursor.fetchall())
       conn.close()
       ```

### 8. processus avec RPA (Robotic Process Automation)
   Python peut être utilisé avec des outils de RPA comme **UiPath** pour automatiser des tâches répétitives liées à des interfaces graphiques.

   - **Outils** :
     - **pyautogui** pour automatiser l’interaction avec l’interface utilisateur (cliquer sur des boutons, taper du texte).
     - **Exemple** :
       ```python
       import pyautogui

       pyautogui.write('Automatisation avec Python')
       pyautogui.press('enter')
       ```

