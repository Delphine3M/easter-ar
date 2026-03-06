# 🥚 Easter AR Magic — WebAR Experience

A festival-quality Easter nature AR experience accessible via QR code.
100% free and open-source — no paid platform, no backend required.

---

## Tech Stack

| Library | Version | License | CDN |
|---------|---------|---------|-----|
| [A-Frame](https://aframe.io) | 1.4.2 | MIT | cdnjs |
| [Three.js](https://threejs.org) | (bundled with A-Frame) | MIT | — |
| [qrcode.js](https://github.com/davidshimjs/qrcodejs) | 1.0.0 | MIT | cdnjs |

**Zero backend. Zero tracking. Zero cost.**

---

## Project Structure

```
EasterAR/
├── index.html      ← Welcome / landing page (animated spring theme, QR code on desktop)
├── ar.html         ← Full AR experience (camera + A-Frame Easter scene)
├── manifest.json   ← PWA manifest (installable on home screen)
└── README.md       ← This file
```

---

## What Users Experience

1. **Scan QR code** (or open the URL directly on mobile)
2. **Welcome page** — animated Easter background, feature list, privacy notice
3. **"Allow Camera & Start"** button — explicit permission request with privacy explanation
4. **AR scene activates:**
   - 🥚 **5 floating Easter eggs** — soft pastel colours, gentle float + spin
   - 🐰 **2 spring rabbits** — full procedural geometry, one walks left↔right with a hop, one sits and sways
   - 🦋 **3 butterflies** — pink, blue, yellow; wing-flap animation + smooth orbit paths
   - 🌸 **Spring flowers** — 3 daisies on the ground, swaying gently
   - ✨ **22 pollen particles** — floating upward, fade out, loop
   - 🌿 **28 grass blades** — surrounding ring, wind sway animation
   - Dawn-warm lighting with 5 light sources (ambient + directional + 3 coloured points)
5. **📸 "Take Photo"** — captures video frame + AR overlay, saves locally as PNG

---

## Free Deployment Options

### Option 1 — GitHub Pages (recommended, truly free)

```bash
# 1. Create a new repository on github.com (public, free)

# 2. Push the project
git init
git add .
git commit -m "Initial Easter AR experience"
git remote add origin https://github.com/YOUR_USERNAME/easter-ar.git
git push -u origin main

# 3. Enable GitHub Pages
# Go to: Settings → Pages → Source: Deploy from branch → Branch: main → / (root)
# Your URL will be: https://YOUR_USERNAME.github.io/easter-ar/
```

> **Important:** GitHub Pages serves over HTTPS automatically.
> Camera (`getUserMedia`) requires HTTPS — never works on plain HTTP.

---

### Option 2 — Netlify Drop (fastest, zero CLI)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag the `EasterAR/` folder onto the page
3. Your site is live in seconds at a `*.netlify.app` HTTPS URL

---

### Option 3 — Vercel

```bash
npm i -g vercel
cd EasterAR
vercel --prod
```

---

## Generate Your QR Code

Once deployed, generate a QR code for the welcome page URL.
The **welcome page** (`index.html`) auto-generates its own QR code on desktop
pointing to `ar.html` on the same domain.

For a print-ready QR you can also use free tools:
- [qr-code-generator.com](https://www.qr-code-generator.com)
- [goqr.me](https://goqr.me)

---

## Local Testing (HTTPS required for camera)

```bash
# Option A — Python + mkcert (trusted local HTTPS)
mkcert -install
mkcert localhost
python3 -m http.server 8443 --bind localhost   # or use a proper HTTPS server

# Option B — Node http-server with SSL
npx http-server -S -C cert.pem -K key.pem -p 8443

# Option C — VS Code Live Server (easiest for dev)
# Install "Live Server" extension → right-click index.html → Open with Live Server
```

---

## Privacy & Security

- **Camera** is activated only after the user clicks "Allow Camera & Start"
- **No video is recorded, transmitted or stored** anywhere
- **Photos** are captured client-side via Canvas API and downloaded locally
- **No analytics, no cookies, no third-party trackers**
- All CDN libraries are loaded from `cdnjs.cloudflare.com` (subresource integrity can be added)

---

## Performance Notes

All 3D objects are procedural A-Frame primitives (spheres, cylinders) — no external 3D model files to load. This keeps the experience lightweight:

| Element | Primitives | Notes |
|---------|-----------|-------|
| Each rabbit | ~14 spheres/cylinders | Full procedural character |
| Each butterfly | 5 spheres + 1 cylinder | Wing shapes via scale distortion |
| Each Easter egg | 1 sphere + 0–2 tori | Egg shape via Y scale |
| Flowers (×3) | 5 spheres + 1 cylinder each | Daisy pattern |
| Pollen (22) | 22 spheres | Injected via JS component |
| Grass (28) | 28 cylinders | Injected via JS component |

Tested on mid-range Android phones (Snapdragon 665+) and iPhone SE 2020+.

---

*Built with A-Frame 1.4.2 (MIT) + Three.js · 100% free & open-source*
