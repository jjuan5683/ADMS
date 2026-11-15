# Changelog

## v6.2 — 2026-11-14
- PMCS can be saved **partial** (unchecked items = NOT CHECKED) and **without an operator**. A partial PMCS never improves the previous vehicle status.
- New categories: **ENGINE START** (no-start / hard start, charging, wait-to-start) and **A/C** (blower, cools, leaks/compressor).
- **REQUESTS** in each PMCS: NATO slave start, recovery, maintenance support, parts, battery, tire, fuel, replacement vehicle, other — with who it went to, time and status (requested / completed / cancelled). The app suggests a NATO request when a start fault is logged.
- **Collapse**: minimize/expand all categories, auto-minimize completed categories, per-category counter.
- Writing assistant: **multiple suggestions** can be combined (one fault per line); new start and A/C terms.
- **Per-vehicle PMCS history** as evidence: last 100 records, 30-day strip, recorded by, timestamp, SHA-256 integrity hash; requests can be closed from history. "PMCS (n)" button on each fleet card.
- **PMCS PDF export**: DETAILED (one page per PMCS) or COMPACT (all vehicles in one table plus vehicles without PMCS) for today, last 7 days, this month or a custom date range.
- More realistic vehicle silhouettes (HMMWV with/without turret, M1152, LMTV, MTV, Van, MHC, M149, trailer).
- Unclassified faults (no symbol) = AMBER.

## v6.1 — 2026-11-14
- Real-name/DOD ID seed removed; vehicle location; reference image + photo per model; PMCS by family with DA PAM 750-8 symbols; ES/EN writing assistant; vector PMCS PDF; Letter-size and escaping fixes on the export PDF.

## Package 6.2-pwa
- Added `manifest.webmanifest`, `sw.js`, `icons/`, `404.html`, `robots.txt`, `.github/workflows/safety-check.yml`.
- `index.html` (this package only): CSP now allows `worker-src 'self'`, `manifest-src 'self'`, `img-src 'self'`; added manifest/icon links, `noindex`, and service-worker registration (http/https only). `connect-src 'none'` unchanged. The standalone `ADMS-v6.2.html` is not modified.
- Pre-commit hook and `.gitignore` allow `icons/*.png`.
