# TapStar Customer Platform

Plateforme complète pour cartes NFC/QR dynamiques avec administration, activation sécurisée par PIN et comptes clients.

## Installation locale

1. Installez Node.js 20+ et PostgreSQL.
2. Créez une base `tapstar`.
3. Copiez `.env.example` vers `.env` et remplacez les secrets.
4. Exécutez `npm install`.
5. Chargez les variables de `.env`, puis lancez `npm run migrate`.
6. Lancez `npm run dev`.

Le frontend utilise le port Vite et l’API le port 4000. En production, exécutez `npm run build`, `npm run migrate`, puis `npm start`.

## Déploiement

Sur Render ou Railway, ajoutez un service PostgreSQL et les variables de `.env.example`. La commande de build est `npm install && npm run build && npm run migrate`; la commande de démarrage est `npm start`. Définissez `PUBLIC_URL` avec votre domaine HTTPS final.

## Flux

- L’administrateur génère un lot de QR avec un PIN unique visible une seule fois.
- Un QR non réclamé ouvre `/activate/:short_code`.
- Le client vérifie le PIN, crée son compte/se connecte, puis choisit son lien.
- Un QR actif redirige vers ce lien et incrémente les scans.
- Le client peut ensuite modifier le lien ou désactiver sa carte.
