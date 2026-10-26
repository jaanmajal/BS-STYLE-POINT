# BS-STYLE POINT RC TIME ATTACK — S1 v26

Files in this package:
- `index.html` — Race Control
- `results.html` — Public results leaderboard
- `firebase-config.js` — preconfigured Firebase Web App settings and default Event ID (`bs1`)
- `logo.jpg` — TECH-ARTS CRAWLER logo

## Publish with GitHub Pages
1. Upload all four files to the root of your existing GitHub repository.
2. Keep `index.html`, `results.html`, `firebase-config.js`, and `logo.jpg` in the same root folder.
3. In Settings → Pages, publish branch `main` from `/(root)`.
4. Open the website over HTTPS.

## Changes in v26
- Correction penalty controls are compact, one-row controls with − / + buttons.
- Correction time and gate fields are blank until the organiser chooses a correction action; they are cleared after a successful correction or clear action.
- The saved result details remain visible as informational text.
- The correction controls use their own driver and SS selectors and do not alter the live stopwatch.
- Stopwatch resets to `00:00.00` after a result is saved, when no eligible driver is selected, and when a new driver is selected.
- The correction action requires an explicit choice before it can be saved.

Security reminder: the Firebase web configuration is browser-visible. Protect race data with appropriate Firebase Authentication and Realtime Database rules. Never include organizer passwords in these files.
