# Guide de Déploiement - E-Commerce Django

## Important: GitHub Pages vs Hébergement Django

**GitHub Pages ne peut PAS héberger d'applications Django** car:
- GitHub Pages = Sites statiques uniquement (HTML/CSS/JS)
- Django = Application backend dynamique nécessitant Python/serveur

## Solutions de déploiement (Gratuites)

### Option 1: Railway.app (Recommandé - Le plus simple)

#### Étapes:

1. **Créer un compte sur Railway**
   - Aller sur https://railway.app/
   - Se connecter avec GitHub

2. **Déployer le projet**
   ```bash
   # Pousser votre code sur GitHub d'abord
   git add .
   git commit -m "Prêt pour déploiement"
   git push origin master
   ```

3. **Sur Railway:**
   - Cliquer sur "New Project"
   - Choisir "Deploy from GitHub repo"
   - Sélectionner votre repository
   - Railway détectera automatiquement Django

4. **Configurer les variables d'environnement**
   Dans Railway, aller dans Variables:
   ```
   SECRET_KEY=votre-nouvelle-cle-secrete-aleatoire
   DEBUG=False
   ALLOWED_HOSTS=*.railway.app
   ```

5. **Railway déploiera automatiquement!**
   - URL fournie: `https://votre-projet.railway.app`
   - Déploiement automatique à chaque push

#### Commandes après déploiement:
```bash
# Dans Railway CLI ou Web Terminal:
python manage.py migrate
python manage.py createsuperuser
python manage.py collectstatic --noinput
```

---

### Option 2: Render.com

#### Étapes:

1. **Créer un compte sur Render**
   - Aller sur https://render.com/
   - Se connecter avec GitHub

2. **Créer un nouveau Web Service**
   - Cliquer sur "New +"
   - Choisir "Web Service"
   - Connecter votre repository GitHub

3. **Configuration du service:**
   ```
   Name: ecommerce-project
   Environment: Python 3
   Build Command: cd ecommerce && pip install -r ../requirements.txt
   Start Command: cd ecommerce && gunicorn ecommerce.wsgi:application
   ```

4. **Variables d'environnement:**
   ```
   SECRET_KEY=votre-cle-secrete
   DEBUG=False
   ALLOWED_HOSTS=*.onrender.com
   PYTHON_VERSION=3.11.0
   ```

5. **Déployer**
   - Cliquer sur "Create Web Service"
   - Render construira et déploiera automatiquement

---

### Option 3: PythonAnywhere (Gratuit avec limitations)

1. **Créer un compte**
   - https://www.pythonanywhere.com/
   - Plan gratuit disponible

2. **Upload du code**
   - Via Git ou upload direct
   - Configuration manuelle nécessaire

3. **Configuration**
   - Créer un virtual environment
   - Installer les dépendances
   - Configurer WSGI

---

## GitHub Actions - CI/CD

Le fichier `.github/workflows/django-ci.yml` est déjà configuré pour:

✅ Tester le code à chaque push
✅ Vérifier les migrations
✅ Linter le code Python
✅ Tester sur plusieurs versions de Python

### Ce que fait le workflow:

1. **Tests automatiques** sur chaque push/PR
2. **Vérification de la qualité du code**
3. **Validation des migrations Django**

### Résultat:

- Badge de statut sur GitHub
- Notifications d'erreurs
- Garantie de qualité du code

---

## Déploiement automatique avec Railway

### Configuration dans Railway:

1. **Aller dans Settings → Deploy**
2. **Activer "Auto-Deploy"**
3. **Choisir la branche: master**

### Workflow complet:

```bash
# 1. Faire vos modifications
git add .
git commit -m "Nouvelle fonctionnalité"

# 2. Pousser sur GitHub
git push origin master

# 3. Automatiquement:
# - GitHub Actions teste le code
# - Si les tests passent ✅
# - Railway déploie automatiquement 🚀
```

---

## Fichiers de configuration créés

### ✅ Procfile
Indique comment lancer l'application:
```
web: cd ecommerce && gunicorn ecommerce.wsgi --log-file -
```

### ✅ runtime.txt
Spécifie la version Python:
```
python-3.11.0
```

### ✅ requirements.txt
Contient toutes les dépendances + production:
- gunicorn (serveur production)
- whitenoise (fichiers statiques)
- python-decouple (variables env)

### ✅ .github/workflows/django-ci.yml
Tests automatiques sur chaque push

---

## Configuration de production

### Variables d'environnement requises:

```bash
SECRET_KEY=une-cle-tres-longue-et-aleatoire-de-50-caracteres
DEBUG=False
ALLOWED_HOSTS=votre-domaine.com,*.railway.app
```

### Générer une SECRET_KEY:

```python
from django.core.management.utils import get_random_secret_key
print(get_random_secret_key())
```

---

## Checklist avant déploiement

- [ ] Code poussé sur GitHub
- [ ] `.env` dans `.gitignore` ✅
- [ ] `requirements.txt` à jour ✅
- [ ] `Procfile` créé ✅
- [ ] `runtime.txt` créé ✅
- [ ] Variables d'environnement configurées sur la plateforme
- [ ] `DEBUG=False` en production
- [ ] `ALLOWED_HOSTS` configuré
- [ ] Migration de la base de données effectuée

---

## Commandes utiles après déploiement

```bash
# Migrations
python manage.py migrate

# Créer un superuser
python manage.py createsuperuser

# Collecter les fichiers statiques
python manage.py collectstatic --noinput

# Voir les logs (Railway)
railway logs

# Shell Django (Railway)
railway run python ecommerce/manage.py shell
```

---

## Support et dépannage

### Erreur: "Application error"
- Vérifier les logs de la plateforme
- Vérifier que `DEBUG=False`
- Vérifier `ALLOWED_HOSTS`

### Erreur: "Static files not loading"
- Exécuter `collectstatic`
- Vérifier la configuration de WhiteNoise

### Erreur: "Database error"
- Vérifier que les migrations sont appliquées
- Vérifier la configuration de la base de données

---

## Recommandation finale

**Pour ce projet, je recommande Railway.app:**
- ✅ Gratuit
- ✅ Déploiement automatique
- ✅ Simple et rapide
- ✅ Supporte Django nativement
- ✅ Base de données PostgreSQL incluse
- ✅ CLI disponible

**Déploiement en 2 minutes!** 🚀
