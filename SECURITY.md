# Security / OPSEC policy

1. **No operational data in Git.** No real names, DOD ID, license numbers, bumper lists, PMCS records, backups (`.json`), Excel, CSV or PDF exports. The repo holds only the empty app and documentation.
2. **Make the repository Private.** The code holds no data, but the vehicle list and unit workflow still show who uses it. (GitHub Pages on a private repo requires a paid plan; otherwise use the app as a local file.)
3. **The app has no network access.** CSP `connect-src 'none'`, no CDNs, no analytics. Do not add external scripts, fonts or images.
4. **Before every commit** the hook in `.githooks/pre-commit` (enable it with `git config core.hooksPath .githooks`):
   - blocks `.json`, `.xlsx`, `.xls`, `.csv`, `.pdf` and image files outside `docs/`;
   - confirms the seed data is empty (`INITIAL_DRIVERS = []`, `INITIAL_VEHICLES = []`);
   - blocks 10-digit DOD ID patterns in seed data.
5. **On devices:** turn on the Vault (password) on shared tablets, lock when not in use, and keep encrypted backups in an authorized location only (not personal cloud).
6. **Photos:** the app re-compresses them and removes EXIF/GPS. Do not upload photos showing bumper numbers, plates or the facility.
7. **Reporting:** if real data is committed by mistake, do not only delete the file. Rewrite history (`git filter-repo`), rotate the backup password, and notify the chain of command / unit security manager.

## PWA / GitHub Pages notes
- GitHub Pages sites are public even when the repo is private (unless your plan supports private Pages). The app is blank, so this is acceptable; **never** put data in the repo.
- CSP in this package is relaxed only for same-origin `worker-src`, `manifest-src` and `img-src`. Network access stays blocked (`connect-src 'none'`); the CI check fails if that changes or if a CDN is added.
- The service worker caches only static app files. Data stays in localStorage / IndexedDB of the browser and is not cached or synced.
- `safety-check.yml` repeats the pre-commit rules on GitHub, because a local hook can be skipped.
