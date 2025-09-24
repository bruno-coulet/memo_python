
En Python, le module **`pathlib`** permet de gérer les chemins de fichiers et de dossiers de manière claire, puissante et moderne. Il remplace avantageusement le module `os` grâce à une approche orientée objet.

---
### 🌿 **1. Créer des chemins :**

```python
from pathlib import Path 
# Répertoire courant
project_root = Path(".")
# Chemin absolu
print(project_root.resolve())  # Affiche le chemin complet
```

---

### 📁 **2. Naviguer dans les dossiers :**


```python
# Accéder à un sous-dossier ou un fichier
data_dir = project_root / "data"
print(data_dir)  # "./data"
```

💡 **`/`** est utilisé pour construire les chemins, ce qui est beaucoup plus lisible que `os.path.join()`.

---

### 📜 **3. Vérifier l'existence ou le type de fichier :**

```python
print(data_dir.exists())       # True si le chemin existe print(data_dir.is_dir())        # True si c'est un dossier print(data_dir.is_file())       # True si c'est un fichier
```

---
### 🏷️ **4. Lire et écrire des fichiers :**


```python
file = data_dir / "example.txt"

# Lire un fichier
print(file.read_text())
# Écrire dans un fichier
file.write_text("Hello, World!")
```


---
### 🔍 **5. Parcourir les fichiers et dossiers :**


```python
# Lister les fichiers dans un répertoire
for file in data_dir.iterdir():
	print(file)  # Affiche chaque fichier et dossier dans ./data
```

---

### ⚡ **6. Chemins absolus et parents :**

```python
print(file.resolve())  # Chemin absolu
print(file.parent)     # Dossier parent
print(file.name)       # Nom du fichier
print(file.suffix)     # Extension(.txt)
print(file.stem)       # Nom sans extension (example)
```

---

### ✅ **7. Créer des répertoires :**

```python
new_dir = project_root / "new_folder"
new_dir.mkdir(exist_ok=True)  # Crée le dossier s'il n'existe pas
```

---

**👉 Pourquoi utiliser `pathlib` ?**

- ✅ Plus lisible et élégant que `os.path`
- ✅ Compatibilité multiplateforme (Windows, Linux, Mac)
- ✅ Gestion simple des chemins relatifs et absolus