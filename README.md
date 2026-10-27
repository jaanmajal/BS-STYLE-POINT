# BS-STYLE POINT RC TIME ATTACK S1 v27.3

Updated from the organizer-edited v27.1 `index.html`, preserving the organizer's wording changes and existing v27.1 features, then adding the per-SS Driver Draw & Spin feature from v27.2.

## Included files
- `index.html` — edited wording + Driver Draw & Spin
- `results.html` — public results page carried forward from v27.2
- `firebase-config.js` — existing Firebase configuration
- `logo.jpg` — existing logo

## Driver Draw & Spin
- Separate random running order for each SS
- Saved draw order and lock state in the same Firebase Event ID
- Uses the selected SS draw order in the main driver dropdown
- Draw/lock controls require the existing admin PIN
- Draw is locked automatically once a result is saved for that SS
- Driver registration/removal is blocked after any draw lock or saved SS result
- If an SS has a draw, its order must be locked before timing can start
- Removing a driver also clears their local penalty records and removes them from unlocked draw lists
- Draw order and lock data are included in backup/import sync queue

## Preserved from organizer-edited file
- Wording edits in the uploaded `index(EDITED).html`
- Save-result confirmation animation
- Main-screen penalty plus-only controls
- Penalty tap cooldown
- Existing scoring, correction, DNF gate progress, Firebase, offline queue and result-save safeguards

Please test the draw synchronization on two devices using different SS before competition. Live Firebase behavior was not tested in this build environment.
