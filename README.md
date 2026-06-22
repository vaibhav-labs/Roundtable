# Roundtable — PWA

A conversation card game. Pick a themed deck, set the table, optionally lay down ground rules, and deal prompts one card at a time — with a little drama (animation, whoosh, haptic buzz). Installable on phone and tablet, works offline.

## What's in this folder

| File | Purpose |
|---|---|
| `index.html` | The whole app (HTML + CSS + JS + all 29 decks / 1,216 prompts) |
| `manifest.json` | Web app manifest — name, colors, icons, standalone display |
| `sw.js` | Service worker — caches the app shell so it runs offline after first load |
| `icon-192.png`, `icon-512.png` | App icons |
| `icon-maskable-512.png` | Maskable icon (Android adaptive) |

> This needs to be served over **http(s)** for install/offline to work — a service worker won't register from a `file://` page. The deploy options below all serve it correctly.

## Share it — pick one

### Option A — GitHub Pages (free, permanent URL)
1. Create a new repository (e.g. `roundtable`) at https://github.com/new
2. Upload every file in this folder to the repo root (drag-and-drop into the GitHub web "Add file → Upload files" works).
3. Repo **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder = `/ (root)`, Save.
4. After a minute your shareable link is: `https://<your-username>.github.io/roundtable/`

### Option B — Netlify Drop (fastest, no account needed)
1. Go to https://app.netlify.com/drop
2. Drag this whole folder onto the page.
3. You get an instant public URL to share. (Free Netlify account lets you keep/rename it.)

### Option C — Cloudflare Pages / Vercel
Connect the GitHub repo from Option A, or drag-drop the folder. No build command, no framework — it's a static site, so default settings work.

## Installing on a device
- **iPhone / iPad:** open the link in Safari → Share → *Add to Home Screen*.
- **Android:** open in Chrome → menu → *Install app* / *Add to Home Screen*.

Launches full-screen, portrait, with its own icon.

## Updating later
Edit `index.html` (decks live in `const DECKS = [...]`, guardrails in `const RULES = [...]`), re-upload, and bump the `CACHE` name in `sw.js` (e.g. `roundtable-v2`) so devices pull the new version.

## Notes
- Fonts (Fraunces, Space Grotesk) load from Google Fonts on first visit, then the service worker caches them for offline use. For guaranteed first-load-offline, self-host the two fonts.
