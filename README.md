# Assa Crochet

Site vitrine et boutique pour **Assa Crochet**, pièces au crochet faites main par Annette. Le site inclut un espace d'administration intégré permettant de tout gérer soi-même : produits, photos, bannières, réglages — sans écrire une ligne de code.

## 🌐 Aperçu

- **Site public** : collection, configurateur sur-mesure, galerie, FAQ, commande directe sur WhatsApp.
- **Espace pro intégré** : accessible via le bouton 🔒 *Espace pro* en bas du site (ou dans le menu mobile ☰), pour tout modifier sans toucher au code.
- **Léger et sans dépendance** : `index.html` (HTML, CSS, JavaScript) + un dossier `assets/` pour les photos et vidéos de démonstration. Aucun serveur, aucune installation, aucune dépendance externe requise pour fonctionner.

## 🚀 Démarrer en local

Aucune installation nécessaire. Il suffit d'ouvrir le fichier directement :

```bash
open index.html      # macOS
start index.html      # Windows
```

Ou double-cliquez simplement sur `index.html` dans l'explorateur de fichiers.

## 🔑 Accès à l'espace pro

En bas de n'importe quelle page, cliquez sur **🔒 Espace pro**.

| Identifiant | Mot de passe |
|---|---|
| `assa234` | `an2121` |

⚠️ Ces identifiants sont vérifiés côté navigateur (pas de serveur). C'est suffisant pour un usage personnel, mais **si vous activez Firebase** (voir plus bas), pensez à créer un vrai compte avec e-mail/mot de passe : ce sera alors la méthode de connexion utilisée automatiquement.

## 📦 Déployer gratuitement

### Option 1 — GitHub Pages (avec ce dépôt)
1. Poussez ce dépôt sur GitHub (voir plus bas).
2. Allez dans **Settings → Pages**.
3. Source : **Deploy from a branch**, branche `main`, dossier `/ (root)`.
4. Votre site sera en ligne à `https://<votre-utilisateur>.github.io/<nom-du-repo>/`.

### Option 2 — Netlify Drop (le plus simple, sans compte GitHub)
1. Allez sur [app.netlify.com/drop](https://app.netlify.com/drop).
2. Glissez-déposez `index.html` dans la page.
3. Vous obtenez une adresse en ligne instantanément.

## 🔥 Aller plus loin : base de données en ligne (Firebase)

Par défaut, le site fonctionne en **mode local** : vos modifications sont enregistrées dans le navigateur utilisé. Pour un vrai site professionnel où toutes vos modifications apparaissent instantanément pour tous vos visiteurs, avec des photos illimitées, suivez le guide complet :

👉 **[firebase-setup.md](./firebase-setup.md)**

Tant que vous n'avez pas suivi ce guide, **aucun script externe n'est chargé** — le site reste 100 % autonome et fonctionne sans aucune configuration.

## 🗂️ Structure du dépôt

```
assa-crochet/
├── index.html            → le site complet (public + espace pro)
├── assets/
│   ├── images/            → photos par défaut (produits, logo)
│   └── videos/             → vidéos par défaut de la bannière
├── firebase-setup.md     → guide pas-à-pas pour la base de données en ligne
├── firestore.rules       → règles de sécurité à coller dans Firebase (base de données)
├── storage.rules         → règles de sécurité à coller dans Firebase (photos)
└── README.md             → ce fichier
```

`index.html` reste très léger (une centaine de Ko) car les photos/vidéos par défaut sont désormais des fichiers séparés dans `assets/`, chargés normalement par le navigateur. Gardez le dossier `assets/` à côté de `index.html` — sans lui, le site s'affiche mais sans les photos de démonstration.

## 🧵 Fonctionnalités de l'espace pro

- **Produits** : ajout, modification, suppression, mise en avant "coup de cœur"
- **Bientôt disponible** : pièces à venir + la "prochaine pépite" en grand format
- **Bannière à la une** : photos et vidéos qui défilent en haut du site
- **Galerie communauté** : mur photo "Portées par vous"
- **Réglages** : numéro WhatsApp, compte Instagram, logo, photo principale
- **Sauvegarde** : export/import JSON, réinitialisation aux valeurs d'origine

## 🛠️ Personnalisation rapide

Sans même toucher au code, vous pouvez tout changer depuis l'espace pro. Pour des changements plus profonds (couleurs, textes fixes, structure), ouvrez `index.html` dans un éditeur de texte — les sections sont commentées et organisées par blocs (`/* ============ NOM DE LA SECTION ============ */`).

---

Créé avec 🤍 pour Annette.
