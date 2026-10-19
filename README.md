# Rapière — site vitrine (GitHub Pages)

Site statique : un seul `index.html`, une feuille de style, aucun build.

## Structure

```
rapiere-site/
├── index.html              ← la page
├── css/
│   └── style.css           ← tout le style (couleurs en haut du fichier, dans :root)
├── assets/
│   ├── logo/
│   │   ├── logo.svg        ← REMPLACER par le logo épée (garder le nom)
│   │   └── favicon.svg     ← REMPLACER par une version carrée du logo
│   ├── images/
│   │   ├── hero-poster.jpg ← image affichée avant/à la place de la vidéo
│   │   ├── og-image.jpg    ← image d'aperçu quand le lien est partagé (LinkedIn, WhatsApp…)
│   │   └── team/
│   │       ├── lucas-cousin.jpg
│   │       └── daniel-naji.jpg
│   └── video/
│       ├── hero.mp4        ← vidéo du hero (obligatoire)
│       └── hero.webm       ← même vidéo en WebM (optionnel, plus léger)
├── .nojekyll               ← indique à GitHub Pages de servir les fichiers tels quels
└── README.md
```

Les noms de fichiers sont déjà branchés dans `index.html` : dépose les fichiers avec **exactement ces noms** et ils apparaissent. Tant qu'un fichier manque, la page affiche un emplacement vide propre (pas d'image cassée).

## Formats recommandés

| Fichier | Format | Dimensions | Poids max conseillé |
|---|---|---|---|
| `logo.svg` | SVG (fond transparent) | hauteur ~36 px à l'affichage | — |
| `favicon.svg` | SVG carré | 32 × 32 | — |
| `hero-poster.jpg` | JPG | 1920 × 1080 (16:9) | 300 Ko |
| `og-image.jpg` | JPG | 1200 × 630 | 300 Ko |
| `team/*.jpg` | JPG | 800 × 600 (4:3) | 150 Ko |
| `hero.mp4` | MP4 H.264, **sans son** | 1920 × 1080, 10–20 s en boucle | 8 Mo |
| `hero.webm` | WebM VP9 | idem | 5 Mo |

- La vidéo démarre seule, sans son et en boucle : c'est obligatoire pour l'autoplay sur mobile.
- Les photos d'équipe s'affichent en noir et blanc automatiquement (filtre CSS).
- GitHub refuse les fichiers de plus de 100 Mo, et un dépôt Pages doit rester sous 1 Go : compresse la vidéo.

Compression vidéo (si ffmpeg est installé) :

```
ffmpeg -i source.mov -an -vf scale=1920:-2 -c:v libx264 -crf 26 -preset slow -movflags +faststart assets/video/hero.mp4
ffmpeg -i source.mov -an -vf scale=1920:-2 -c:v libvpx-vp9 -crf 36 -b:v 0 assets/video/hero.webm
```

## À compléter dans `index.html`

- `contact@example.com` (3 occurrences) → l'adresse de contact réelle.

## Mise en ligne

1. Crée un dépôt GitHub (par ex. `rapiere-site`) et pousse ces fichiers à la racine.
2. Settings → Pages → Source : *Deploy from a branch*, branche `main`, dossier `/ (root)`.
3. Le site est en ligne quelques minutes plus tard sur `https://<ton-compte>.github.io/rapiere-site/`.
4. Domaine perso (ex. `rapiere.eu`) : Settings → Pages → Custom domain, puis configure le DNS chez ton registrar comme indiqué par GitHub.

## Avant publication publique

- Vérifier l'intitulé exact de chaque reconnaissance (NATO, Airbus, Arquus) et l'accord des organisations pour être citées.
- Un dépôt GitHub Pages gratuit est **public** : ne pas y mettre de documents internes ou de médias non validés pour diffusion.
