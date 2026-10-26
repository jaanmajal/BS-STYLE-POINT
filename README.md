# BS-STYLE POINT RC TIME ATTACK — S1 v27 Reliable Online

Complete package for Race Control and public results.

## Files
- `index.html` — Race Control, offline queue and combined result/penalty correction workflow.
- `results.html` — Dark public results dashboard with Overall and SS1–SS4 tabs, driver detail panel and Firebase status.
- `firebase-config.js` — Existing Firebase project configuration. Keep this file in the repository root.
- `logo.jpg` — TEC-ARTS CRAWLER logo.

## S1 v27 correction workflow
1. Open **Backups, import, corrections** and choose a driver and SS.
2. Review **Recorded before correction** and **After correction preview**.
3. Select a new status if needed, or leave status blank to retain the saved status. Enter a new finish time or DNF gate count only if needed.
4. Penalty count inputs are blank by default. Blank means **keep the recorded count**; enter a number to replace the count; enter `0` to remove that penalty type.
5. Press **Save result + penalties together**. The result and penalty data are saved locally together and, when connected, written to Firebase in one multi-path update and verified.
6. After saving, inputs clear and the before/after comparison remains visible. Changing the selected driver or stage starts a fresh correction.

The exact driver/stage currently being timed or awaiting SAVE RESULT cannot be corrected until that run is resolved. Corrections to other drivers do not interrupt the active timer.

## Online/offline safety
- Local data and a persistent pending queue are retained in browser storage.
- Online corrections are written to Firebase together and verified by reading the saved values back.
- If offline or a write fails, the changes remain queued for retry. Export a JSON backup if the queue-storage warning appears.
- Before competition, test online save, offline save, reconnect, and public leaderboard verification on the actual mobile devices.

## GitHub Pages deployment
Upload the files to the repository root and enable GitHub Pages from `main` / root. Use the same Firebase project and Event ID on every marshal device. Public results use `results.html?event=YOUR_EVENT_ID`.

The Firebase configuration and organizer credentials are not to be changed by this update. Do not share organizer passwords.
