# The Hill Slayer — Austin Cap10K Trainer (iPhone App)

A self-contained web app of your wife's 46-week, Saturday-only training plan,
packaged so it installs on an iPhone home screen and runs full-screen and
**offline** (works out on the trail with no signal).

## What's in this folder

| File | Purpose |
|------|---------|
| `index.html` | The app itself (the original plan + mobile + offline support) |
| `manifest.webmanifest` | Makes it installable with a name + icon |
| `service-worker.js` | Caches everything so it works offline after the first load |
| `icons/` | App icons (lime bolt over hills) |
| `serve.js` | Tiny local server, only used for testing on a computer |

Her progress (completed weeks + notes) is saved on her phone via `localStorage`,
so it persists between sessions. It is per-device and not synced.

## Getting it onto her iPhone (recommended: free hosting)

An installable PWA must be opened from an `https://` web address. The easiest
no-account way:

1. Go to **https://app.netlify.com/drop** in a browser.
2. Drag this entire `cap10k-app` folder onto the page.
3. Netlify gives you a public link (e.g. `https://random-name.netlify.app`).
4. Text/AirDrop that link to your wife.
5. On her iPhone, she opens the link **in Safari**, taps the **Share** button,
   then **"Add to Home Screen."**
6. A "Hill Slayer" icon appears on her home screen. Tapping it launches the app
   full-screen, no browser bars.

> Have her open it once **with internet** so the offline cache fills. After that
> it runs without a connection.

Other equivalent hosts: GitHub Pages, Vercel, Cloudflare Pages.

## Testing locally on this Mac

```
node serve.js
# then open http://localhost:8080
```

## Updating the plan later

Edit `index.html`, then bump `CACHE_VERSION` in `service-worker.js`
(e.g. `hillslayer-v1` → `hillslayer-v2`) so phones pull the new version.
Re-upload the folder to the same host.
