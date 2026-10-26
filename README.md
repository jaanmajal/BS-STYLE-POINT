# BS-STYLE POINT RC TIME ATTACK - S1 v26 Reliable Online Package

Files included:
- `index.html` - Race Control with online green section borders, persistent local-first result saving, server-confirmed writes, an event-specific pending upload queue, reconnect retry, visible pending status, and before-leave warnings.
- `results.html` - Dark professional public leaderboard with Overall/SS1-SS4 tabs, filters, driver detail panel, Firebase live status, and Event ID display.
- `firebase-config.js` - Existing Firebase Web App configuration and default Event ID (`bs1`).
- `logo.jpg` - TEC-ARTS CRAWLER logo.

## Publish
1. Extract the ZIP.
2. Replace the four files in the root of the existing GitHub repository.
3. Keep all four files together in the repository root.
4. Publish `main` from `/(root)` in GitHub Pages settings.
5. Open the site over HTTPS. Use the same Event ID on all Race Control devices; the public link includes it, for example `results.html?event=bs1`.

## Offline and sync safeguards
- Race data is written to local browser storage before upload is attempted.
- Every change is queued per Event ID if Firebase is disconnected or the write fails.
- Queued writes are retried after network restoration, tab visibility restoration, and Firebase reconnection.
- Successful writes are read back from Firebase before being marked confirmed.
- A visible banner shows the number of pending changes.
- The page warns before leaving while a result is awaiting save or uploads are pending.
- Sync conflicts are not silently overwritten; the organiser must confirm whether a queued local value should replace a different online value.
- If local and Firebase data differ without a recorded pending queue, the app saves a safety snapshot and asks before loading Firebase data.
- JSON backup export includes pending changes for the active Event ID.

## Important limitations
This reduces the risk of missing results but cannot guarantee zero loss if the browser's storage is cleared, the device is damaged, or storage quota is exhausted. Export JSON backups regularly, and verify `SAVED ONLINE` before assuming Firebase has confirmed a result. Local mode does not synchronize between devices until you connect to the same Firebase project and Event ID.

Firebase Web App configuration is visible in browser code by design. Never include organizer passwords in these files. Keep Firebase Authentication and Realtime Database rules configured to restrict writes to authorized accounts.
