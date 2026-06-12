# WC 2026 Family Sweepstake

A single-page web app for your family sweepstake. Shared live state via Firebase.
Results auto-update from football-data.org every 10 minutes.

---

## Setup (one-time, takes ~10 minutes)

### 1. Firebase — shared live state

1. Go to https://console.firebase.google.com and sign in with a Google account
2. Click **Add project**, name it (e.g. `wc2026-sweepstake`), skip Analytics
3. Once created, click **Build → Realtime Database** in the left sidebar
4. Click **Create database**, choose any region, select **Start in test mode**
5. Click **Project settings** (gear icon top-left) → **Your apps** → **</> Web**
6. Register the app (any nickname), then copy the `firebaseConfig` object
7. Open `index.html` in any text editor and paste the values into `window.FIREBASE_CONFIG`

### 2. Football data — live results

1. Go to https://www.football-data.org and click **Get free API key**
2. Register with an email address (free, no card needed)
3. Copy your API token from the dashboard
4. Paste it into `window.FOOTBALL_API_KEY` in `index.html`

### 3. Publish to GitHub Pages

1. Create a new public GitHub repository (e.g. `wc2026-sweepstake`)
2. Push `index.html` and `README.md` to the `main` branch
3. Go to **Settings → Pages → Source** and select **main branch / root**
4. GitHub will give you a URL like `https://yourusername.github.io/wc2026-sweepstake`
5. Share that URL with the family — everyone sees the same live leaderboard

---

## How it works

- **Draw**: one person enters names and runs the draw. Firebase stores the result — everyone 
  sees it instantly.
- **Scores**: auto-fetched from football-data.org every 10 minutes. Hit 🔄 to refresh manually.
  Manual overrides are preserved across auto-refreshes.
- **Leaderboard**: live, same for everyone, no refresh needed.

---

## Security note

Firebase is set to "test mode" (public read/write). This is fine for a family sweepstake 
— the only risk is someone clearing the draw, which you can recover by re-running it.
If you want to lock it down after the draw, change the Firebase rules to `".write": false`.
