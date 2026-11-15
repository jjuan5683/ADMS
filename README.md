# ADMS — Army Driver Management System

Offline, single-file web app for company-level **Master Driver Management**, vehicle readiness and **PMCS** tracking (PRNG).

> **This repository contains NO data.** The app starts blank. All soldier, vehicle and PMCS data lives only in the browser of each device (localStorage / IndexedDB, optionally encrypted). Nothing is sent to the internet: the page's Content-Security-Policy blocks every network connection (`connect-src 'none'`).

## Use

| Option | How |
|---|---|
| Local (recommended for field use) | Download `index.html` and open it in Chrome or Edge. Works with no internet. |
| GitHub Pages (installable PWA) | Settings → Pages → Branch `main` / root. Open `https://<user>.github.io/<repo>/`. The page loads from GitHub, but your data stays in that browser. After the first load it works offline; on the phone use *Add to Home Screen* / *Install*. |

### Load your data (restore backup)
1. Open the app → **JSON (import)** → select your backup file (`.json`, encrypted if you set a password).
2. Data is stored **per browser and per address**: a backup restored on `file://…/index.html` will not appear on the GitHub Pages address, or the other way around. Restore on each device and address you use.
3. **Never commit backups, Excel files or PDFs to this repo.** `.gitignore` and the pre-commit hook block them.

## Modules
OPS dashboard · Drivers (licenses, qualifications, limitations) · Fleet (status, location MOTOR POOL / UNIDAD / FMS / OTHER, reference image) · Missions / trip tickets · **PMCS** (checklist by vehicle family, DA PAM 750-8 symbols, partial PMCS, requests such as NATO slave start, ES/EN fault-writing assistant, per-vehicle history with integrity hash, detailed and compact PDF reports) · Fuel log · Audit log · Vault (encryption) · Encrypted backups.

## Supported vehicles
M1079A1P2 · M1151A1 · M1165A1 · M1078A1P2 · M1083A1 · M1084A1 MHC · M1152A1 · M149A2 · Cargo Trailer ¾ ton (plus generic models).

## Important
- The PMCS checklist is **generic by vehicle family — must be confirmed against each TM -10** (see `docs/PMCS-SPEC.md`).
- PMCS PDFs are worksheets for DA Form 5988-E / GCSS-Army entry; they do not replace the official form.
- Do not store medical diagnoses, medications, VA data, convoy routes, frequencies/COMSEC, weapons assignments or coordinates.

## PWA files
`manifest.webmanifest` (name, icons, standalone) · `sw.js` (caches only the app shell; network-first, so a new `index.html` is picked up when online; never touches your data) · `icons/` (192, 512, maskable, Apple touch) · `404.html` · `robots.txt` (no indexing). On `file://` the service worker is skipped and the app works as before.

To release an update, bump `CACHE` in `sw.js` (e.g. `adms-shell-v6.3-1`) in the same commit as the new `index.html`.

## Developer setup
```bash
git config core.hooksPath .githooks   # enable the safety check before every commit
```

See `SECURITY.md` and `CHANGELOG.md`.
