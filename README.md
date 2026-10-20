# Orge & Houblon Verdun — site vitrine

Site statique, sans build. Tous les fichiers sont à la racine.

| Fichier | Rôle |
|---|---|
| `index.html` | Site complet (HTML, CSS, JS) |
| `hero.mp4` | Vidéo de fond de l'accueil, aussi utilisée par segments dans les sections |
| `intro.mp4` | Intro : verre qui se remplit + écriture manuscrite |
| `hero.jpg` / `intro.jpg` | Images affichées pendant le chargement des vidéos |
| `favicon.svg` | Icône d'onglet |

## Mise en ligne
- **GitHub Pages** : Settings → Pages → Source : `main` / `/ (root)`.
- **Vercel / Netlify** : importer le repo, aucun réglage (Framework : Other, pas de build).

## Remplacer une vidéo
Garder le même nom de fichier. Encodage conseillé :
```
ffmpeg -i source.mp4 -vf "scale=-2:720" -an -c:v libx264 -crf 25 -g 30 -pix_fmt yuv420p -movflags +faststart hero.mp4
```
Si `hero.mp4` change, mettre à jour les attributs `data-seg="début,fin,vitesse"` des vidéos de section dans `index.html`.
