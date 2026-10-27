# BS-STYLE POINT RC TIME ATTACK S1 v27.5.1

This is based on S1 v27.5. It includes only two small updates requested by the organiser:

1. Uses the existing TEC-ARTS CRAWLER logo as the browser tab icon on Race Control and Public Results (`favicon.png`).
2. Makes the “New Race — Clear All Race Data” section collapsible and collapsed by default. The existing reset password, confirmations, Firebase checks and reset behaviour are unchanged.

No concurrent SS dispatch logic was added in this build. Existing driver draw, late entry, edit driver name, scoring, penalties, DNF gate progress, correction workflow, offline queue and save safeguards are retained from v27.5.

## Files
- `index.html` — Race Control
- `results.html` — Public Results
- `firebase-config.js` — existing Firebase configuration
- `logo.jpg` — full logo
- `favicon.png` — browser tab icon made from the logo
