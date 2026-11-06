# Unhookd: complete source backup

Unhookd is an ADHD-friendly recovery companion for people who are stopping or cutting down on alcohol, tobacco, cannabis or other substances. This archive contains the full working prototype, as published on 6 November 2026, together with its assets, documentation and project material.

© 2026 Ambika Thangaraju. All rights reserved. See `COPYRIGHT.txt`.

## What's in this folder

| Path | What it is |
| --- | --- |
| `index.html` | **The app, byte-for-byte as published** (Unhookd v2). One self-contained file holding all HTML, CSS, JavaScript and SVG art. Loads its fonts from Google Fonts and the QR-code libraries from public CDNs. |
| `index-selfhosted.html` | The same file with exactly three URLs changed so that it loads fonts and QR libraries from `vendor/` instead of the internet. Nothing else is different (see "Two ways to run it" below). |
| `vendor/` | Local copies of the fonts (Nunito, Baloo 2) and the two QR libraries (qrcodejs, jsQR), with their licences. Used by `index-selfhosted.html`. |
| `assets/illustrations/` | 55 standalone SVG files exported from the running app: Finn the fish (every accessory and mood), the journey map, the nine place stickers, the party-effect icons, every Learn story picture and the logo. |
| `source-reference/` | The same app split into `css/styles.css`, `js/app.js` and `index.html` for easier reading and editing. The code is copied verbatim; it also runs. |
| `versions/v1-earlier-prototype/` | The earlier published prototype (v1), kept as a backup. |
| `docs/` | Technical and ownership documentation, plus project material (see below). |
| `netlify.toml`, `404.html` | Netlify configuration. |
| `COPYRIGHT.txt` | Copyright notice. |

### Documentation (`docs/`)

| File | Contents |
| --- | --- |
| `docs/ARCHITECTURE.md` | How the app is built: structure, state, storage, browser APIs, external services. |
| `docs/FILE_INVENTORY.md` | Every file in this archive with its size, SHA-256 checksum and purpose. |
| `docs/THIRD_PARTY_LICENSES.md` | External libraries, fonts and services, and their licences. |
| `docs/NOT_EXPORTED_AND_DEPENDENCIES.md` | What could not be exported, what depends on Claude or on outside services, and known limitations. |
| `docs/VERIFICATION_REPORT.md` | What was tested before packaging, how, and the results. |

## Two ways to run it

1. **`index.html` (exact copy).** Identical to the published app. It needs an internet connection for the Google Fonts and for drawing or scanning QR codes. Without internet the app still works, but text falls back to system fonts and the QR image is replaced by the plain code.
2. **`index-selfhosted.html` (no outside downloads).** Identical code, but fonts and QR libraries come from `vendor/`. It needs nothing from the internet to run.

The only differences between the two files:

| `index.html` | `index-selfhosted.html` |
| --- | --- |
| `<link>` tags to `fonts.googleapis.com` / `fonts.gstatic.com` | `<link rel="stylesheet" href="vendor/fonts/fonts.css">` |
| `https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js` | `vendor/qrcodejs/qrcode.min.js` |
| `https://cdn.jsdelivr.net/npm/jsqr@1.4.0/dist/jsQR.min.js` | `vendor/jsqr/jsQR.js` (same version, unminified build) |

To make the self-hosted version the default page, rename it to `index.html` (keep the original under another name, for example `index-original.html`).

## Run it on your computer

Any static web server works. With Python installed:

```
cd UNHOOKD_COMPLETE_SOURCE_BACKUP
python3 -m http.server 8080
```

Then open `http://localhost:8080/` (or `http://localhost:8080/index-selfhosted.html`) in a browser. Opening the file directly by double-clicking also works for most features, but camera/clipboard features behave best over `http://localhost` or `https://`.

## Deploy to Netlify

No build step is needed. This is a static site.

**Option A: drag and drop (simplest)**
1. Unzip `UNHOOKD_COMPLETE_SOURCE_BACKUP.zip`.
2. Sign in at https://app.netlify.com.
3. Go to **Sites** and choose **Add new site → Deploy manually**.
4. Drag the unzipped `UNHOOKD_COMPLETE_SOURCE_BACKUP` folder onto the drop area.
5. Netlify gives you a URL such as `https://your-site-name.netlify.app`. Open it on your phone and test.

**Option B: from a Git repository**
1. Put the contents of this folder in a GitHub, GitLab or Bitbucket repository.
2. In Netlify choose **Add new site → Import an existing project** and pick the repository.
3. Leave the build command empty and set the publish directory to `.` (the included `netlify.toml` already does this).
4. Deploy.

**Option C: Netlify CLI**
```
npm install -g netlify-cli
cd UNHOOKD_COMPLETE_SOURCE_BACKUP
netlify deploy          # preview deploy
netlify deploy --prod   # production deploy
```

### GitHub Pages

This repository can also be served by GitHub Pages: Settings → Pages → Deploy from a branch → `main`, folder `/ (root)`. The `.nojekyll` file makes Pages serve every file as it is.

Project documents (MIT Solve answers, business plan) are kept out of this public repository and live only in the private backup.

### Routing

The app uses hash routes (`#today`, `#journey`, `#care`, `#learn`, `#me`), so no server-side routing is required. `netlify.toml` still sends unknown paths to `index.html` so a mistyped address opens the app instead of an error.

## Important notes

- **Data stays in each browser.** The app saves everything in the browser's `localStorage` under the key `focus-recovery-v2`. Data entered in the Claude-hosted version does not move to your Netlify site, and data on one phone does not appear on another. There is no import or export feature yet.
- **It is a prototype.** Pro is simulated (no payment), emergency numbers are prototype data to be confirmed, and medical text is to be reviewed by a clinician. See `docs/NOT_EXPORTED_AND_DEPENDENCIES.md`.
- **Independent deployment has been tested on a local static web server only**, not on Netlify itself. See `docs/VERIFICATION_REPORT.md`.
