# Setup Guide — Multi-Crop Tool

> A single-file HTML tool to upload one image and crop it for every social media platform at once.

Made by **Sudais Alam**.

---

## Project Overview

**Multi-Crop Tool** is a self-contained web app (`multicrop.html`) for creators and social media managers. Upload one image and instantly preview correctly-sized crops for Instagram, YouTube, LinkedIn, Twitter, Pinterest, TikTok, and Facebook — then download each crop (or all of them as a ZIP). It includes smart auto-crop, custom aspect ratios, and quick filters.

---

## Prerequisites

- A modern web browser (Chrome, Edge, Firefox, Safari) — that's it.
- An internet connection the first time you load it (for CDN-hosted fonts/icons/JSZip), unless you vendor those assets locally.

No Node, no build tools, no server required.

---

## Installation

```bash
# 1. Clone
git clone https://github.com/sudaisalamboy/multi-crop-in-one.git
cd multi-crop-in-one

# 2. That's it — open the file directly
#    Double-click multicrop.html, or:
```

---

## Running Locally

### Option A — Open directly
Double-click `multicrop.html` (it opens via `file://`). Works for all core features.

### Option B — Serve via a tiny local server (recommended)
```bash
# Python 3
python3 -m http.server 8080

# or Node
npx serve .
```
Then visit **http://localhost:8080/multicrop.html**.

> Serving via HTTP is recommended so the browser allows canvas image operations consistently across all origins.

---

## Project Structure

```
.
├── multicrop.html          # Entire app: markup, CSS, and JS in one file
├── README.md
├── SETUP.md
└── preview/preview.png
```

---

## Customization

- **Add a new platform preset** — open `multicrop.html`, find the `platforms` array (in the `<script>` section) and add an entry:
  ```js
  { name: 'My Platform', aspect: '1-1', icon: 'facebook', iconClass: 'facebook-icon' }
  ```
  plus a matching `.aspect-X-Y` CSS rule if the ratio is new.
- **Change brand colors** — edit the `:root` CSS variables at the top of `<style>`.
- **Run fully offline** — replace the CDN links (Poppins, Font Awesome, JSZip) with local copies in the same folder and update the `href`/`src` paths.

---

## Deployment

Because it's a single static file, you can host it anywhere:

- **GitHub Pages** — push to a repo and enable Pages on the `main` branch root.
- **Netlify / Vercel / Cloudflare Pages** — drag-and-drop the folder, or connect the repo.
- **Any static host** (InfinityFree, your own server) — just upload `multicrop.html`.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| **Cropped image won't download / blank** | Make sure the image finished loading before cropping; some browsers block canvas `toDataURL` on `file://` for tainted images — serve via `python3 -m http.server`. |
| **"Download all as ZIP" does nothing** | JSZip failed to load from CDN (offline/blocked). Vendor `jszip.min.js` locally and update the `<script src>`. |
| **Icons look like squares** | Font Awesome CDN blocked; vendor the CSS + webfonts locally. |
| **Drag-and-drop not working** | Use a modern browser; ensure no other element overlays the upload area. |
| **Fonts fall back to default** | Google Fonts blocked; either allow the network or vendor Poppins locally. |
| **Custom ratio not rendering** | Add the matching `.aspect-X-Y` CSS rule for any new ratio value you introduce. |

---

## Credits

Made by **Sudais Alam**.
