# E-Commerce Django Project

Un projet e-commerce simple et élégant développé avec Django, présentant des produits électroniques avec un système de catégories.
C'est un petit projet réalisé pour tester de nouvelles choses avec le Framework

## Apparence 


<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/70583ca9-a36b-43a0-a2d5-e935aaf3fc76" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/039277b8-f7e3-45f9-8595-be8fec9aa1c5" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/5748de92-ac7c-4077-9a5c-b3f3c7d7b48c" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/4d7eaa76-ca88-4694-918f-19f5dbea0a8e" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/3120f9b1-726f-41d2-bc6f-41e1d5b02515" />

## Fonctionnalités

- Liste et détail des produits
- Système de catégories
- Interface moderne avec Bootstrap 5
- Design responsive
- Gestion des images de produits
- Interface d'administration Django
- Système de stock

## Technologies utilisées

- Python 3.x
- Django 5.2.4
- Bootstrap 5
- Font Awesome
- SQLite (base de données)
- Pillow (gestion d'images)

## Installation

### Prérequis

- Python 3.8 ou supérieur
- pip (gestionnaire de paquets Python)

### Étapes d'installation

1. Cloner le repository
```bash
git clone <url-du-repo>
cd ecommerce_project
```

2. Créer un environnement virtuel
```bash
python -m venv venv
```

3. Activer l'environnement virtuel

**Windows:**
```bash
venv\Scripts\activate
```

**Linux/Mac:**
```bash
source venv/bin/activate
```

4. Installer les dépendances
```bash
pip install -r requirements.txt
```
6. Effectuer les migrations
```bash
cd ecommerce
python manage.py migrate
```

7. Créer un superutilisateur
```bash
python manage.py createsuperuser
```

8. Lancer le serveur de développement
```bash
python manage.py runserver
```

9. Accéder à l'application
- Site web: http://127.0.0.1:8000/
- Interface admin: http://127.0.0.1:8000/admin/

## Structure du projet

```
ecommerce_project/
├── ecommerce/              # Projet Django principal
│   ├── ecommerce/         # Configuration du projet
│   │   ├── settings.py    # Paramètres Django
│   │   ├── urls.py        # URLs principales
│   │   └── wsgi.py
│   ├── products/          # Application produits
│   │   ├── models.py      # Modèles (Product, Category)
│   │   ├── views.py       # Vues
│   │   ├── urls.py        # URLs de l'app
│   │   ├── admin.py       # Configuration admin
│   │   ├── templates/     # Templates HTML
│   │   └── static/        # Fichiers statiques (CSS)
│   ├── images/            # Images uploadées
│   └── manage.py
├── venv/                  # Environnement virtuel
├── requirements.txt       # Dépendances Python
├── .gitignore
├── .env.example
└── README.md
```
