# Bhavnagar Satsang Center — Setup Guide (JSONBin Edition)

Firebase has been replaced with **JSONBin.io** — a free, simple REST API.
No SDK. No complex console setup. Just one API key.

---

## Step 1 — Get a free JSONBin API Key (2 minutes)

1. Go to **https://jsonbin.io** → click **Sign Up** (email or Google)
2. After login, click your profile icon (top-right) → **API Keys**
3. Click **+ Create API Key** → give it any name → copy the key
4. Open `config.js` in this folder and paste it:

```js
export const JSONBIN_API_KEY = "YOUR_KEY_HERE";
export const JSONBIN_BIN_ID  = "";   // leave empty for now
```

That's the only setup needed before deploying.

---

## Step 2 — Deploy to GitHub Pages

### 2a. Create a GitHub repository

1. Go to https://github.com → **New repository**
2. Name it: `bhavnagar-satsang-center`
3. Set it to **Public** (required for free GitHub Pages)
4. Do NOT initialize with a README

### 2b. Push your code

```bash
git init
git add admin.html index.html config.js SETUP.md
git commit -m "Initial deploy — Bhavnagar Satsang Center"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/bhavnagar-satsang-center.git
git push -u origin main
```

### 2c. Enable GitHub Pages

1. Repo → **Settings** → **Pages**
2. Source: branch `main`, folder `/ (root)` → **Save**
3. Wait ~2 minutes → your site is live at:
   - Projector: `https://YOUR_USERNAME.github.io/bhavnagar-satsang-center/`
   - Admin:     `https://YOUR_USERNAME.github.io/bhavnagar-satsang-center/admin.html`

---

## Step 3 — First-time Submit (one-time only)

1. Open `admin.html` on your Android phone
2. Write a test notice → tap **✅ Submit Notices**
3. A green banner appears showing your **Bin ID** (looks like `64abc123def456`)
4. Copy that Bin ID → open `config.js` → paste it:

```js
export const JSONBIN_BIN_ID = "64abc123def456";
```

5. Commit and push again:
```bash
git add config.js
git commit -m "Add Bin ID"
git push
```

After this, both pages are fully set up permanently. You never need to do this again.

---

## How to use the app

### Admin (Notice Writer) — on Android phone

Open: `https://YOUR_USERNAME.github.io/bhavnagar-satsang-center/admin.html`

- Tap **"સૂચના ઉમેરો"** to add a notice point
- Type in Gujarati (Gboard → Globe icon → ગુ) OR paste from WhatsApp
- Tap **"✅ Submit Notices"** — projector screen auto-updates within 4 seconds
- If internet fails: tap **"🔗 Backup Link"** → share via WhatsApp → presenter opens that URL

### Presenter (Projector) — on laptop

Open: `https://YOUR_USERNAME.github.io/bhavnagar-satsang-center/`

- Screen auto-refreshes every 4 seconds — no reload needed
- Press **← →** arrow keys or click on-screen arrows to move between slides
- A small "Updated: HH:MM" chip appears when new notices arrive

---

## File structure

```
bhavnagarcenter/
├── index.html    ← Projector / presentation view
├── admin.html    ← Mobile admin (notice writer)
├── config.js     ← JSONBin API key + Bin ID (edit this)
└── SETUP.md      ← This file
```

---

## Troubleshooting

| Problem | Solution |
|---|---|
| "Load Error" on projector | Check that JSONBIN_BIN_ID is set in config.js and re-deployed |
| "API Key paste karo" on admin | Open config.js and set JSONBIN_API_KEY |
| Slides not updating | Normal 4-second poll delay; wait briefly |
| Backup link too long | Normal — URL encodes all Gujarati text; WhatsApp handles it fine |
| 403 / Unauthorized error | Double-check the API key in config.js |
