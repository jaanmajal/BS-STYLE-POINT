# BS-STYLE POINT RC TIME ATTACK — S1 v26 (Online Border + Redesigned Results)

Files in this package:
- `index.html` — Race Control, based on S1 v26 with bold green section borders while connected to Firebase and original borders while offline.
- `results.html` — redesigned dark public results dashboard with Overall/SS1–SS4 tabs, driver search/status filters, tap-to-view driver performance, Firebase connection status and live updates.
- `firebase-config.js` — preconfigured Firebase Web App settings and default Event ID (`bs1`).
- `logo.jpg` — TECH-ARTS CRAWLER logo.

## Publish with GitHub Pages
1. Extract this ZIP.
2. Upload all four files to the root of your existing GitHub repository, replacing the previous copies.
3. Keep `index.html`, `results.html`, `firebase-config.js`, and `logo.jpg` together in the repository root.
4. In Settings → Pages, publish branch `main` from `/(root)`.
5. Open the site over HTTPS. The public results page reads the Event ID from the URL, for example `results.html?event=bs1`.

## Included behavior
- Race Control remains the S1 v26 system with green section borders when the Firebase connection is active; offline state uses the original border styling.
- Public results uses the updated dark professional design and shows the selected Firebase Event ID instead of a fixed event date or venue.
- Public results supports Overall and SS1–SS4 views, driver search, status filters, driver detail panel, and Firebase live updates.

Security reminder: Firebase web configuration is browser-visible. Protect race data with appropriate Firebase Authentication and Realtime Database rules. Never include organizer passwords in these files.
