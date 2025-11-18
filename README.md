# E-Commerce Django Project

Un projet e-commerce simple et élégant développé avec Django, présentant des produits électroniques avec un système de catégories.
C'est un petit projet réalisé pour tester de nouvelles choses avec le Framework

## Apparence


<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/31916dee-bb29-4e12-8cc9-d1f9146568b2" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/90d8692c-6711-4657-af95-c1a0d6377e9f" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/24c3371e-6d86-4888-b805-5e18414d80a2" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/466cf0dc-747a-4637-9023-01729f39d8cb" />
<img width="1919" height="1079" alt="Image" src="https://github.com/user-attachments/assets/6d0b86c2-91b7-4f06-ad9d-41b798c3b61f" />


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
