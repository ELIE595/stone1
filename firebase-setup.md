# Configurer Firebase (base de données gratuite en ligne)

Ce guide vous permet de faire passer le site du **mode local** (vos modifications ne sont visibles que sur votre appareil) au **mode en ligne** : toutes vos modifications apparaissent instantanément pour tous vos visiteurs, sur tous les appareils, avec des photos illimitées.

C'est entièrement gratuit pour un site de cette taille (offre gratuite "Spark" de Firebase).

Tant que vous n'avez pas terminé ce guide, le site continue de fonctionner normalement en mode local — rien n'est cassé entre-temps.

---

## Étape 1 — Créer un projet Firebase

1. Allez sur [console.firebase.google.com](https://console.firebase.google.com)
2. Connectez-vous avec un compte Google
3. Cliquez sur **Ajouter un projet**
4. Donnez-lui un nom (ex : `assa-crochet`)
5. Vous pouvez désactiver Google Analytics (pas nécessaire)
6. Cliquez sur **Créer le projet** et attendez quelques secondes

## Étape 2 — Activer la base de données (Firestore)

1. Dans le menu de gauche, section **Build**, cliquez sur **Firestore Database**
2. Cliquez sur **Créer une base de données**
3. Choisissez **Mode production**
4. Choisissez une région proche de vous (ex : `eur3` pour l'Europe/Afrique)
5. Une fois créée, allez dans l'onglet **Règles** et remplacez tout le contenu par celui du fichier [`firestore.rules`](./firestore.rules) fourni dans ce dépôt
6. Cliquez sur **Publier**

## Étape 3 — Activer le stockage des photos (Storage)

1. Menu de gauche → **Storage** → **Commencer**
2. Choisissez **Mode production**, puis la même région que Firestore
3. Onglet **Règles** → remplacez le contenu par celui du fichier [`storage.rules`](./storage.rules) fourni dans ce dépôt
4. Cliquez sur **Publier**

## Étape 4 — Activer la connexion sécurisée (Authentication)

1. Menu de gauche → **Authentication** → **Commencer**
2. Onglet **Sign-in method** → activez **E-mail/Mot de passe**
3. Onglet **Users** → **Add user**
4. Entrez une vraie adresse e-mail que vous possédez, et choisissez un mot de passe solide
5. C'est ce compte que vous utiliserez désormais pour vous connecter à l'espace pro (à la place de `assa234` / `an2121`)

## Étape 5 — Récupérer vos clés de configuration

1. Cliquez sur l'icône ⚙️ à côté de **Aperçu du projet** (en haut à gauche) → **Paramètres du projet**
2. Descendez jusqu'à **Vos applications**
3. Cliquez sur l'icône **`</>`** (Web)
4. Donnez un nom à l'application (ex : `assa-crochet-web`) et cliquez sur **Enregistrer l'application**
5. Copiez l'objet `firebaseConfig` qui s'affiche — il ressemble à ceci :

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "assa-crochet.firebaseapp.com",
  projectId: "assa-crochet",
  storageBucket: "assa-crochet.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef"
};
```

## Étape 6 — Coller vos clés dans `index.html`

1. Ouvrez `index.html` avec un éditeur de texte (Bloc-notes, TextEdit, VS Code…)
2. Cherchez `REMPLACER_MOI` (Ctrl+F ou Cmd+F) — il y a 6 occurrences
3. Remplacez chacune par la valeur correspondante copiée à l'étape 5
4. Enregistrez le fichier

Exemple avant/après :

```js
// Avant
const firebaseConfig = {
  apiKey: "REMPLACER_MOI",
  authDomain: "REMPLACER_MOI.firebaseapp.com",
  ...
};

// Après
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "assa-crochet.firebaseapp.com",
  ...
};
```

## Étape 7 — Mettre en ligne

Reportez-vous au [README.md](./README.md) pour déployer via GitHub Pages ou Netlify.

## Étape 8 — Tester

1. Ouvrez votre site en ligne
2. Cliquez sur **Espace pro**
3. Connectez-vous avec l'e-mail et le mot de passe créés à l'étape 4 (le champ affichera automatiquement "Adresse e-mail")
4. Ajoutez une photo test — elle doit maintenant s'envoyer vers Firebase Storage (vous pouvez le vérifier dans la console Firebase, section Storage)
5. Ouvrez le site depuis un autre appareil ou navigateur : vos modifications doivent y apparaître aussi

---

## Comment ça fonctionne techniquement

- **Sans configuration** : le site ne charge aucun script Firebase et fonctionne entièrement en local (`localStorage` du navigateur).
- **Avec configuration** : au chargement, le site détecte que `firebaseConfig` a été rempli, charge dynamiquement les scripts Firebase nécessaires, puis bascule sur Firestore (données) et Firebase Storage (photos), avec synchronisation en temps réel entre tous les appareils.
- **En cas de problème** (pas de connexion internet, erreur Firebase), le site retombe automatiquement en mode local sans planter.

## Limites de l'offre gratuite Firebase

Largement suffisantes pour une boutique artisanale :
- **Firestore** : 1 Gio de stockage, 50 000 lectures/jour, 20 000 écritures/jour
- **Storage** : 5 Gio de stockage, 1 Gio de téléchargement/jour
- **Authentication** : illimité pour l'e-mail/mot de passe
- **Hosting** (si vous l'utilisez) : 10 Gio de transfert/mois

Si vous dépassez un jour ces limites, c'est plutôt bon signe : votre boutique cartonne 🎉 — il sera alors temps de passer à l'offre payante à l'usage (`Blaze`), qui reste très abordable.
