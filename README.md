# Application Disponibilités 2026

Application HTML statique permettant à plusieurs personnes d'ajouter et consulter leurs disponibilités jusqu'au 31 décembre 2026. Les données sont stockées dans Cloud Firestore et les utilisateurs sont connectés avec l'authentification anonyme Firebase.

## 1. Créer le projet Firebase

1. Créer un projet dans la console Firebase.
2. Ajouter une application Web.
3. Activer **Authentication > Sign-in method > Anonymous**.
4. Créer une base **Cloud Firestore**.
5. Copier l'objet `firebaseConfig` fourni par Firebase dans `index.html`.
6. Publier les règles du fichier `firestore.rules` dans l'onglet Firestore Rules.

Ne laissez pas Firestore en mode test. Le mode test autorise temporairement des accès trop larges.

## 2. Publier sur GitHub Pages

1. Créer un dépôt GitHub.
2. Ajouter à la racine : `index.html`, `firestore.rules`, `firebase.json`, `README.md`.
3. Dans GitHub, ouvrir **Settings > Pages**.
4. Choisir **Deploy from a branch**, branche `main`, dossier `/root`.
5. Ajouter le domaine GitHub Pages dans **Firebase Authentication > Settings > Authorized domains**.

## 3. Variante Firebase Hosting

Avec Firebase CLI installé :

```bash
firebase login
firebase use --add
firebase deploy --only firestore:rules,hosting
```

## Sécurité et usage entreprise

- La configuration Web Firebase n'est pas un mot de passe. La sécurité dépend surtout de Firebase Authentication et des règles Firestore.
- Cette version utilise l'authentification anonyme. Pour identifier réellement les personnes, remplacez-la par un fournisseur d'identité approuvé.
- Les noms, équipes, commentaires et disponibilités sont visibles par tous les utilisateurs authentifiés de l'application.
- Pour des données professionnelles Michelin, faites valider l'hébergement, le fournisseur d'identité, la classification des données et les règles d'accès selon les politiques internes avant mise en production.
- N'enregistrez aucune donnée sensible ou confidentielle dans ce prototype.

## Fonctionnalités

- Calendrier de septembre à décembre 2026
- Statuts Disponible, À confirmer, Indisponible
- Commentaire facultatif
- Filtre par personne
- Indicateurs de synthèse
- Suppression limitée au créateur de la réponse
- Mise à jour en temps réel via Firestore
- Interface responsive mobile et ordinateur
