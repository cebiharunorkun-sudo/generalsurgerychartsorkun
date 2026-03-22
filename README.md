# SurgAtlas PWA — Deployment Guide

## What's in this folder

```
surgatlas-pwa/
├── index.html          ← Main app (84 flowcharts + glossary)
├── manifest.json       ← PWA manifest (app name, icons, theme)
├── sw.js               ← Service worker (offline caching)
├── icons/              ← App icons (72px to 512px + maskable)
│   ├── icon-72x72.png
│   ├── icon-96x96.png
│   ├── icon-128x128.png
│   ├── icon-144x144.png
│   ├── icon-192x192.png
│   ├── icon-192x192-maskable.png
│   ├── icon-384x384.png
│   ├── icon-512x512.png
│   └── icon-512x512-maskable.png
└── README.md           ← This file
```

## Quickest deployment: GitHub Pages (free, 2 minutes)

1. Create a GitHub account (if you don't have one) at github.com
2. Create a new repository: click "+" → "New repository"
   - Name: `surgatlas` (or anything)
   - Set to **Public**
   - Click "Create repository"
3. Upload all files in this folder to the repository root
   - Click "uploading an existing file" on the repo page
   - Drag the entire contents of this folder (not the folder itself)
4. Enable GitHub Pages:
   - Go to Settings → Pages
   - Source: "Deploy from a branch"
   - Branch: `main`, folder: `/ (root)`
   - Click Save
5. Your app will be live at: `https://yourusername.github.io/surgatlas/`

## Install on Android

Once hosted, open the URL in Chrome on your Android phone:

- **Automatic**: An install banner will appear at the bottom of the screen — tap "Install"
- **Manual**: Tap the Chrome menu (⋮) → "Install app" or "Add to Home Screen"

The app will:
- Appear on your home screen with the SurgAtlas icon
- Launch fullscreen (no browser chrome)
- Work completely offline after first visit
- Show a green "● Offline Ready" badge in the topbar

## Install on iPhone/iPad

1. Open the URL in Safari
2. Tap the Share button (□↑)
3. Tap "Add to Home Screen"
4. Tap "Add"

Note: iOS PWAs have some limitations vs Android (no install prompt banner, limited background sync).

## Alternative hosting options

### Netlify (free, drag & drop)
1. Go to app.netlify.com
2. Drag this entire folder onto the deploy area
3. Done — you get a URL like `random-name.netlify.app`
4. (Optional) Set a custom domain in site settings

### Vercel (free)
1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in this folder
3. Follow prompts — deployed in seconds

### Any web server
Just serve this folder from any HTTPS web server. PWAs require HTTPS (except localhost for testing).

Local testing: `python3 -m http.server 8000` then open `http://localhost:8000`

## Updating the app

When you update `index.html` and redeploy:
1. Increment the version in `sw.js` (change `surgatlas-v1` to `surgatlas-v2`)
2. Users will automatically get the new version on next visit
3. The service worker will download the new files in the background

## Customisation

- **App name**: Edit `manifest.json` → `name` and `short_name`
- **Theme color**: Edit `manifest.json` → `theme_color` and `background_color`
- **Icons**: Replace files in `icons/` (keep the same filenames and sizes)
