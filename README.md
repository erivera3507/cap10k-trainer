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

## Live app

**https://erivera3507.github.io/cap10k-trainer/**

Hosted free on GitHub Pages from the `main` branch of this repo.

### Getting it onto her iPhone

1. Text/AirDrop her the link above.
2. She opens it **in Safari** (must be Safari, not Chrome).
3. Taps the **Share** button → **"Add to Home Screen."**
4. A "Hill Slayer" icon appears on her home screen. Tapping it launches the app
   full-screen, with no browser bars.

> Have her open it once **with internet** so the offline cache fills. After that
> it runs without a connection (e.g. out on a run).

## Testing locally on this Mac

```
node serve.js
# then open http://localhost:8080
```

## Updating the plan later

1. Edit `index.html`.
2. Bump `CACHE_VERSION` in `service-worker.js` (e.g. `hillslayer-v2` →
   `hillslayer-v3`) so installed phones pull the new version.
3. Commit and push to `main` — GitHub Pages redeploys automatically in a minute
   or two.

```
git add -A && git commit -m "Update plan" && git push
```
