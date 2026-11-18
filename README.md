# Keta Packing List

A shared packing checklist for two (or more) people. Everyone gets their own checkbox on every item and can see what the others have ticked, live. Anyone can add or remove items and sections.

Hosted free on GitHub Pages. The shared data lives in a free Firebase Realtime Database.

## Setup (about 10 minutes)

### 1. Create the database
1. Go to https://console.firebase.google.com and sign in with a Google account.
2. **Add project** (any name, e.g. `keta-list`). You can turn off Google Analytics.
3. In the left menu: **Build → Realtime Database → Create Database**. Pick a location, then start in **locked mode**.
4. Open the **Rules** tab, paste the contents of `database.rules.json`, and click **Publish**.

### 2. Get your config
1. **Project settings** (gear icon) → **General** → scroll to **Your apps** → click the web icon `</>`.
2. Register the app (any nickname). Copy the `firebaseConfig` values.
3. Paste them into `config.js`. Make sure `databaseURL` is included. It is shown in the Realtime Database page, e.g. `https://keta-list-default-rtdb.firebaseio.com`.

### 3. Put it on GitHub Pages
1. Create a new GitHub repository and upload `index.html`, `config.js` and `README.md`.
2. **Settings → Pages → Build and deployment**: source = *Deploy from a branch*, branch = `main`, folder = `/ (root)`. Save.
3. After a minute your site is live at `https://YOUR-USER.github.io/YOUR-REPO/`.

### 4. Share it
Open your site. It creates a private list link like `...?list=keta-ab12cd34ef`. Enter your name, then press **Copy link** and send that exact link to your friend. When they open it and enter their name, you will both see each other's boxes.

## Notes
- **Demo mode:** until `config.js` has real Firebase values, the app runs locally in your browser only (nothing is shared).
- **Privacy:** there is no login. Anyone who has the long list link can view and edit it, so only share it with people you trust. Do not put sensitive information in the list. The Firebase `apiKey` in `config.js` is not a secret for this kind of app.
- **Names:** each browser is remembered as one person. A different phone or browser counts as a new person.
- **Starting a new list:** open the site without `?list=...` to get a fresh list with the starter items.
