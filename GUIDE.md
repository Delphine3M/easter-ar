# Easter AR — Guide de maintenance

## Le projet

Expérience AR de Pâques accessible via QR code ou lien direct.
Fichiers dans : `C:\EasterAR`

```
EasterAR/
├── index.html      ← Page d'accueil (animation, QR code sur desktop)
├── ar.html         ← Scène AR (caméra + oeufs, lapins, papillons...)
├── manifest.json   ← PWA (installable sur écran d'accueil)
├── README.md       ← Doc technique
└── GUIDE.md        ← Ce fichier
```

## URL du site

https://delphine3m.github.io/easter-ar/

- Fonctionne sur tout smartphone moderne
- HTTPS automatique (obligatoire pour la caméra)
- Hébergé sur GitHub Pages — gratuit, sans expiration

---

## Compte GitHub

- **URL** : https://github.com/Delphine3M
- **Repository** : https://github.com/Delphine3M/easter-ar
- **Email** : delphine.berte@trimane.fr

---

## Mettre à jour le site

Après avoir modifié un fichier dans `C:\EasterAR`, ouvrir un terminal dans ce dossier et lancer :

```powershell
git add .
git commit -m "Description de la modification"
git push
```

Le site est mis à jour automatiquement en 1-2 minutes.

> Pour ouvrir un terminal dans le dossier : clic droit dans l'explorateur Windows
> sur le dossier EasterAR → "Ouvrir dans le terminal"

---

## S'authentifier sur GitHub (si demandé)

GitHub ne demande plus le mot de passe, il faut un **Personal Access Token**.

1. Aller sur https://github.com/settings/tokens/new
2. Note : `easter-ar`
3. Expiration : 90 days
4. Cocher la case `repo`
5. Cliquer "Generate token" et copier le token (commence par `ghp_...`)
6. Dans le terminal, quand GitHub demande un mot de passe : coller le token
7. Révoquer le token après usage sur https://github.com/settings/tokens

---

## Générer un QR code imprimable

1. Aller sur https://goqr.me
2. Coller l'URL : https://delphine3m.github.io/easter-ar/
3. Télécharger en PNG haute résolution

> La page d'accueil génère aussi un QR code automatiquement quand elle est
> ouverte sur un grand écran (desktop).

---

## Ce que voit l'utilisateur

1. Scanne le QR code ou ouvre le lien sur son téléphone
2. Page d'accueil avec bouton "Start AR Experience"
3. Autorise la caméra
4. La scene AR apparait :
   - 5 oeufs de Paques flottants (360° autour de soi, ~1.5m)
   - 2 lapins (un qui marche, un assis)
   - 3 papillons qui orbitent
   - 3 fleurs au sol
   - Particules de pollen + anneau d'herbe
   - Sol vert opaque (5x5m)
5. Bouton photo pour capturer la scene (sauvegarde en local)

---

## Modifications deja effectuees (mars 2026)

- Elements ramenés de ~2.5m à ~1.5m de rayon autour de la personne
- Jardin reduit de 22x22m à 5x5m et rendu completement opaque
- Positions selfie mises a jour en coherence
