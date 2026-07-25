# Text Tracker — PWA → APK Ready

A polished, installable Progressive Web App that tracks the time since your last received and last sent text messages.

## What's included
- `index.html` — full app with live timers, color states, toast notifications, haptic feedback
- `manifest.json` — PWA install config
- `sw.js` — offline caching service worker
- `icon.svg` / `icon-192.png` / `icon-512.png` — app icons

## Quick test (browser)
1. Open a local server in this folder (important for service worker + install):
   ```
   npx serve .
   # or python3 -m http.server 8080
   ```
2. Open the URL on your phone (same network) or Chrome desktop.
3. Chrome will offer “Install” / “Add to Home Screen”.

## How to make a real APK (recommended methods)

### Option A — PWABuilder (easiest, free)
1. Go to https://www.pwabuilder.com/
2. Enter the URL where you hosted the app (or zip the folder and use their upload if available).
3. Click “Package for stores” → Android → generate the TWA (Trusted Web Activity) APK or AAB.
4. Download the `.apk` or `.aab` and distribute / upload to Play Store.

### Option B — Capacitor (more control)
```bash
npm create @capacitor/app
# choose the folder containing these files as the webDir
npx cap add android
npx cap sync
npx cap open android   # then build signed APK in Android Studio
```

### Option C — Bubblewrap (Google’s tool for TWA)
```bash
npm i -g @bubblewrap/cli
bubblewrap init --manifest=https://your-hosted-url/manifest.json
bubblewrap build
```

## Hosting tips
- Any static host works (GitHub Pages, Netlify, Vercel, Cloudflare Pages, Firebase Hosting, etc.)
- HTTPS is required for install prompt and service worker.
- Once hosted, you can also just share the link and users can “Add to Home Screen”.

## Features
- Live second-by-second timers
- Color shifts (cyan → yellow → red) based on how long you’ve been waiting
- Sent counter that auto-sets timestamp
- One-tap “Now” buttons
- Reset + Copy Status
- Offline capable
- Installable as standalone app on Android & iOS
