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

## Admin, access and pledges (version 2)

- **Admin code:** the person who creates the list is the admin. Their personal link contains a secret admin code (`k=`), so opening it on any phone or browser gives admin rights. Only a fingerprint (hash) of the code is stored in the database. Copy the personal link and keep it somewhere safe.
- **Existing lists:** the original sharer opens the updated site **first**. The app adds an admin code, adds the kitchen lists and asks them to copy their personal link again.
- **List access:** Food and Kitchen lists are visible to everyone. Personal lists (Clothes, Toiletries, ...) are restricted: friends only see them after the admin ticks them under **Lists** next to their name. The admin can also flip any list between "All can see" and "Restricted". The granted lists are stored in the member's record and in the `a=` part of their personal link. After a change, the person is asked to copy their personal link again.
- **Duplicate devices:** the admin presses ✕ next to the duplicate. That device sees "This device was removed" and can paste its real personal link to continue as itself, so the browser is never permanently blocked. The admin can also press **Allow back** under "Removed devices".
- **Admin colours:** only the admin sees other people's ticks in each person's own colour. Everyone else sees one colour.
- **Food pledges:** each food item shows a progress bar for 15 people x 14 days (210 person-days). People pledge "I can bring enough to feed X people for Y days" or "I can bring enough for everyone". The item closes when the total reaches 210. Tinned and canned items just take a number of cans or tins.
- **Kitchen items with limited spots:** items such as "Gas cylinder" (1) or "Sauce pans" (2) close when the spots are taken. The admin can change the limit with the **Limit** button.

**Honest limit:** there are no logins. The admin code, list access and removals are enforced by the app, not by the database, so someone who deliberately edits the database directly could bypass them. For friends and family sharing a link this is normally fine.
