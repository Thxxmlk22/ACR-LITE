# ACR-Lite - Système d'Accréditation

Application web complète pour la gestion des demandes d'accréditation avec système de workflow d'approbation.

## 🚀 Déploiement sur Vercel

### Prérequis
- Compte Vercel (https://vercel.com)
- Compte GitHub (pour l'intégration)

### Étapes de déploiement

1. **Préparer le repository**
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   ```

2. **Pousser sur GitHub**
   - Créez un nouveau repository sur GitHub
   - Ajoutez le remote et poussez le code
   ```bash
   git remote add origin https://github.com/votre-username/votre-repo.git
   git branch -M main
   git push -u origin main
   ```

3. **Déployer sur Vercel**
   - Connectez-vous à Vercel
   - Importez votre repository GitHub
   - Vercel détectera automatiquement la configuration
   - Cliquez sur "Deploy"

### Configuration Vercel

L'application est configurée avec `vercel.json` pour :
- Utiliser le runtime Node.js
- Router toutes les requêtes vers le serveur Express
- Configurer la durée maximale des fonctions

### Variables d'environnement (Optionnel)

Pour la production, configurez ces variables dans Vercel :
- `SESSION_SECRET` : Clé secrète pour les sessions
- `PORT` : Port d'écoute (généralement géré automatiquement par Vercel)

## 📦 Structure du Projet

```
/
├── src/
│   └── server.js          # Serveur principal Express
├── public/                # Fichiers statiques (optionnel)
├── vercel.json           # Configuration Vercel
├── package.json          # Dépendances Node.js
├── .gitignore           # Fichiers à ignorer
└── README.md            # Ce fichier
```

## 🔧 Développement Local

```bash
# Installation des dépendances
npm install

# Démarrage en mode développement
npm run dev

# L'application sera disponible sur http://localhost:3000
```

## 👤 Comptes par Défaut

- **Admin** : admin@example.com / admin123
- **Représentant** : Créez un compte via l'interface d'inscription

## ⚠️ Notes Importantes

- Cette application utilise SQLite en local, mais sur Vercel vous devrez utiliser une base de données externe
- Les fichiers uploadés ne sont pas persistants sur Vercel (utilisez un service de stockage cloud)
- Pour la production, configurez une base de données externe (PostgreSQL, MySQL, etc.)

## 🛠️ Technologies Utilisées

- Node.js + Express
- SQLite (better-sqlite3)
- Multer (gestion des uploads)
- bcrypt (hashage des mots de passe)
- express-session (gestion des sessions)
- Pico CSS (framework CSS minimaliste)
