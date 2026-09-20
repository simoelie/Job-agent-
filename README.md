# Job Agent Mobile V5

Reconstruction propre de Job Agent, pensée pour iPhone via une PWA.

## Fonctions incluses
- Tableau de bord responsive/PWA
- Base SQLite locale
- Import manuel d'offres
- Scoring offre/CV par mots-clés
- 20 familles de postes
- Journal des candidatures et protection contre doublons
- États: trouvée, préparée, validation requise, envoyée, confirmée, échec
- Connexion Gmail OAuth (configuration Google requise)
- Recherche de confirmations de candidature dans Gmail
- Coffre local chiffré pour métadonnées/secrets applicatifs
- Architecture de connecteurs ATS avec mode sûr: aucune tentative de contourner CAPTCHA/MFA
- API REST FastAPI

## Installation
1. Installer Python 3.11+
2. `python -m venv .venv`
3. Activer l'environnement
4. `pip install -r requirements.txt`
5. Copier `.env.example` vers `.env`
6. `uvicorn app.main:app --host 0.0.0.0 --port 8000`
7. Ouvrir `http://localhost:8000`

Pour iPhone, héberger l'application derrière HTTPS puis Safari > Partager > Ajouter à l'écran d'accueil.

## Gmail
Créer des identifiants OAuth Google de type Web Application et renseigner:
- GOOGLE_CLIENT_ID
- GOOGLE_CLIENT_SECRET
- GOOGLE_REDIRECT_URI

Le projet demande un accès Gmail en lecture seule. Les mots de passe Gmail ne sont jamais stockés.

## Sécurité
Cette reconstruction ne contourne ni CAPTCHA, ni MFA, ni protections anti-bot. Les connecteurs ATS doivent respecter les conditions des services. En cas de contrôle humain requis, la candidature passe en `validation_requise`.

## Limite importante
Le code source V4.6 original n'étant pas disponible, ceci est une reconstruction fonctionnelle basée sur les fonctionnalités connues, et non une copie bit-à-bit de V4.6.
