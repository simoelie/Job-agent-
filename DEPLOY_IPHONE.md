# Mise en service iPhone

## 1. Mettre le code sur GitHub
Créez un dépôt privé et téléversez le contenu de ce dossier.

## 2. Déployer sur Render
- New > Web Service
- Connecter le dépôt
- Render détectera `render.yaml`.
- Définir GOOGLE_CLIENT_ID et GOOGLE_CLIENT_SECRET.
- Après le premier déploiement, copier l'URL HTTPS Render.

## 3. Configurer Google OAuth
Dans Google Cloud:
- Activer Gmail API.
- Configurer l'écran de consentement.
- Créer un OAuth Client ID de type Web application.
- URI de redirection autorisée:
  `https://VOTRE-SERVICE.onrender.com/auth/google/callback`
- Dans Render, définir GOOGLE_REDIRECT_URI avec exactement cette URL.
- Redéployer.

## 4. Connecter Gmail
Sur l'iPhone:
- Ouvrir l'URL Job Agent.
- Gmail > Connecter / reconnecter Gmail.
- Autoriser l'accès Gmail en lecture seule.

## 5. Installer comme application iPhone
Safari > Partager > Ajouter à l'écran d'accueil.

## Important
Le stockage SQLite et le fichier de jeton OAuth doivent être placés sur un stockage persistant pour un usage durable. Un service éphémère peut perdre ces données lors d'un redéploiement. Pour une version production durable, utiliser PostgreSQL et un stockage chiffré des jetons.
