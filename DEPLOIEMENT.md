# GUIDE DE DÉPLOIEMENT ACR-LITE SUR VERCEL

## 📋 Prérequis
- Compte GitHub
- Compte Vercel
- Node.js installé localement (pour le développement)

## 🚀 Déploiement sur Vercel

### Étape 1 : Créer un repository GitHub
1. Créez un nouveau repository sur GitHub
2. Initialisez git localement :
```bash
git init
git add .
git commit -m "Initial commit - ACR-Lite app ready for deployment"
```
3. Liez votre repository distant :
```bash
git remote add origin https://github.com/votre-username/votre-repo.git
git branch -M main
git push -u origin main
```

### Étape 2 : Déployer sur Vercel
1. Connectez-vous à [vercel.com](https://vercel.com)
2. Cliquez sur "New Project"
3. Importez votre repository GitHub
4. Vercel détectera automatiquement la configuration :
   - **Framework Preset**: Node.js
   - **Build Command**: Aucun (l'application n'a pas de build step)
   - **Output Directory**: Aucun
   - **Install Command**: `npm install`

### Étape 3 : Configuration Vercel (automatique)
La configuration `vercel.json` est déjà en place :
```json
{
  "version": 2,
  "builds": [
    {
      "src": "src/server.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "src/server.js",
      "methods": ["GET", "POST", "PUT", "DELETE", "PATCH", "OPTIONS", "HEAD"]
    }
  ]
}
```

### Étape 4 : Variables d'environnement (optionnel)
Si nécessaire, ajoutez des variables d'environnement dans Vercel :
- `SESSION_SECRET` : Pour la sécurité des sessions
- `PORT` : Port d'écoute (généralement géré automatiquement par Vercel)

## 🔧 Fonctionnalités déployées

### ✅ Pages d'authentification séparées
- **Connexion** : `/login` - Formulaire de connexion uniquement
- **Inscription** : `/register` - Formulaire de création de compte RO représentant
- **Navigation** : Liens "Se connecter" et "Créer un compte" dans le header

### ✅ Améliorations visuelles
- Statuts colorés avec meilleur contraste (brouillon, soumis, approuvé, rejeté)
- Design cohérent pour les badges et puces d'état

### ✅ Fonctionnalités complètes
- Tableau de bord des demandes d'accréditation
- Workflow d'approval (brouillon → soumis → approuvé/rejeté)
- Zone d'administration pour gérer catégories et codes d'accès
- Upload de photos et documents

## 🐛 Dépannage

### Problèmes courants :
1. **Base de données en lecture seule** : Vercel utilise un système de fichiers en lecture seule
   - Solution : Utiliser SQLite en mémoire ou adapter pour une base de données externe

2. **Stockage des fichiers uploadés** : Vercel ne persiste pas les fichiers entre les déploiements
   - Solution : Utiliser un service de stockage externe (S3, Cloud Storage, etc.)

3. **Variables d'environnement** : Vérifier que toutes les variables nécessaires sont configurées

## 📞 Support
Pour toute question concernant le déploiement, consultez la documentation Vercel :
- [Documentation Vercel Node.js](https://vercel.com/docs/functions/serverless-functions/runtimes/node-js)
- [Configuration Vercel.json](https://vercel.com/docs/projects/project-configuration)

L'application est maintenant prête pour le déploiement en production !
