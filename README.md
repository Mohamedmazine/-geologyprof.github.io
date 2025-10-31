# GéoSite – Geology prof

Un site statique (HTML/CSS/JS) pour présenter des projets de **géologie** : cartes, coupes, affleurements, inventaires paléontologiques et rapports.

- **URL prévue** : https://geologyprof.github.io/
- **Contact** : geologyunivm@gmail.com

---

## 🧭 Arborescence recommandée

```
/ (racine du dépôt)
├── index.html
├── projets.html
├── projet-anticlinal-ifri.html
├── projet-ammonites.html
├── projet-coupe-boumerdes.html
├── mentions.html
├── contact.html
├── site.webmanifest
├── sitemap.xml
├── robots.txt
├── /img
│   ├── icon-192.png
│   ├── icon-512.png
│   └── og-image.jpg
├── /docs         # rapports PDF, coupes, exports HD
├── /maps         # exports qgis2web (Leaflet) ou cartes HTML
└── /data         # CSV, GeoJSON, etc.
```

---

## 🚀 Publication sur GitHub Pages

1. Crée (ou utilise) le dépôt **`geologyprof/geologyprof.github.io`**.
2. Dépose tous les fichiers ci‑dessus à la racine du dépôt.
3. Va dans **Settings → Pages** et assure‑toi que **Source** = `Deploy from a branch`, branche `main`, dossier `/ (root)`.
4. Ouvre **https://geologyprof.github.io/**.

> Astuce : lors d’une mise à jour, pousse tes commits sur `main` et attends le déploiement automatique (quelques secondes).

---

## 🗺️ Données cartographiques (Leaflet / QGIS)

- Les points/lignes/polygones de `index.html` sont dans la variable **`features`** (GeoJSON).
- Pour publier une carte QGIS :
  1. Installe l’extension **qgis2web** et exporte en **Leaflet**.
  2. Copie le dossier exporté sous `/maps/nom-de-ta-carte/`.
  3. Lien depuis une fiche projet (ex. `maps/anticlinal/index.html`).

---

## 🧩 Contenu des pages

- **index.html** : accueil, carte démo, galerie, contact, mentions.
- **projets.html** : liste filtrable (recherche, thématique, année). Les projets se définissent dans le tableau `projects` (en bas du fichier).
- **projet-*.html** : fiches projet prêtes (Ifri, Ammonites, Coupe Boumerdès). Duplique et adapte pour créer d’autres fiches.
- **mentions.html** : page Mentions & Licences (modifie la licence si besoin).
- **contact.html** : formulaire (Formspree, avec fallback `mailto:`).

---

## ✍️ Ajouter un projet

1. Duplique une fiche (ex. `projet-anticlinal-ifri.html`) → renomme‑la `projet-nom.html`.
2. Ouvre **projets.html** et ajoute un objet dans le tableau `projects` :
   ```js
   {
     id: "proj-nom",
     titre: "Titre du projet",
     resume: "Résumé en 1–2 phrases.",
     annee: 2025,
     thematique: ["Cartographie"],
     motscles: ["grès","faille", "Jurassique"],
     localisation: "Wilaya / Pays",
     vignette: "img/ma-vignette.webp",
     liens: { fiche: "projet-nom.html", carte: "maps/ma-carte/index.html", pdf: "docs/mon-rapport.pdf" }
   }
   ```
3. Ajoute tes fichiers dans `/docs`, `/maps`, `/img` et mets à jour les liens.

---

## 🖼️ Images & performance

- Utilise **.webp** pour les vignettes (1200 px max, 70–80 % qualité).
- Évite les images > **500–700 KB** en page d’accueil/projets.
- Donne des **attributs `alt`** descriptifs pour l’accessibilité.

---

## 🔎 SEO & partage social

- Metas **Open Graph** + **Twitter Card** déjà incluses.
- Balises **canonical** + **JSON‑LD** (WebSite, CollectionPage, Article, Breadcrumb).
- **sitemap.xml** & **robots.txt** fournis ; vérifie l’URL `https://geologyprof.github.io/` dans les fichiers.

---

## 📱 PWA (icônes & manifest)

- `site.webmanifest` : personnalise `name`, `short_name`.
- Icônes : `/img/icon-192.png` et `/img/icon-512.png` (déjà générées).

---

## ✉️ Formulaire de contact (Formspree)

- Dans `contact.html`, remplace `YOUR_FORM_ID` par l’ID de ton formulaire :  
  ```html
  <form action="https://formspree.io/f/VOTRE_ID" method="POST">
  ```
- Sans ID, le formulaire basculera automatiquement en **mailto:** vers `geologyunivm@gmail.com` (fallback).

---

## 🛠️ Personnalisation rapide

- **Couleurs** : variables CSS dans `:root` (`--bg`, `--panel`, `--accent`, etc.).
- **Police** : la stack système est utilisée par défaut (rapide). Tu peux charger une Google Font si tu le souhaites.
- **Carte d’accueil** : modifie la variable `features` ou remplace par un iframe issu d’un export qgis2web.

---

## ✅ Check‑list avant publication

- [ ] URL et `canonical` → `https://geologyprof.github.io/`
- [ ] Email de contact : `geologyunivm@gmail.com`
- [ ] `site.webmanifest` à la racine
- [ ] `/img/icon-192.png` / `/img/icon-512.png` / `/img/og-image.jpg`
- [ ] `sitemap.xml` / `robots.txt`
- [ ] Liens `projects[].liens` OK (fiche / carte / PDF)
- [ ] Images compressées (≤ 500–700 KB en pages listées)
- [ ] Mentions & Licences mises à jour

---

## ❓ FAQ

**Q : Je ne vois pas ma carte qgis2web.**  
R : Vérifie les **chemins relatifs** (ex. `maps/anticlinal/index.html`) et que tout le **dossier exporté** est bien poussé.

**Q : Les images ne s’affichent pas.**  
R : Chemin incorrect ou nom de fichier sensible à la casse (`.webp` vs `.WebP`).

**Q : L’aperçu social (OG) ne sort pas.**  
R : Publie les fichiers, puis colle l’URL dans un réseau social. Certains caches peuvent prendre quelques minutes.

**Q : Puis‑je ajouter Google Analytics / Plausible ?**  
R : Oui. Préfère une solution **sans cookies** (ex. Plausible/Matomo en mode anonymisé).

---

## Licence

Sauf mention contraire, © Geology prof – GéoSite.  
Cartes OSM © contributeurs OpenStreetMap (ODbL). Leaflet (BSD-2-Clause).
