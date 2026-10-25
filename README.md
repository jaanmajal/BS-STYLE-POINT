# BS-STYLE POINT RC TIME ATTACK — S1 v14

## Scoring system

- Finishing positions are ranked by **raw elapsed time** (fastest first). Penalties do not add time and do not change the finishing order.
- Base position points: 1st 100, 2nd 95, 3rd 90, 4th 87, 5th 84, 6th 81, 7th 78, 8th 75, 9th 72, 10th 69; the published descending scale continues through 40th, and 40th or lower receives 26 base points.
- Net FINISH points = `max(0, base position points - penalty point deductions)`.
- DNF base points = `max(20, base points for the last registered position - 20)`. Deduct applicable penalty points from the DNF base; minimum 0. DNS = 0.
- Default shared penalty types: Touch = 15 points per tap; Gate violation = 5 points per tap; Roll-over = 5 points per tap. Organisers can change these values before racing in Section 5.
- Each penalty tap snapshots the current point value. Later edits to the penalty setup affect future taps only. Do not penalise the same incident with both added time and point deductions.
- Overall champion: highest accumulated net points. Ties: higher net points in final SS, then more recorded stages, then lower cumulative raw time, then lower race number.

## Publishing / Firebase

1. Upload `index.html`, `results.html`, `firebase-config.js`, `logo.jpg`, and `README.md` to the root of the GitHub repository.
2. GitHub Pages: Settings → Pages → Deploy from a branch → `main` → `/(root)`.
3. Default Event ID: `bs1`. Use the same Firebase project and Event ID on all timing devices. Organizer email/password are entered at connect time and are not persisted by the app.
4. Configure Firebase Realtime Database rules carefully. Do not use public write access. Public spectators need read access only; writes should require authenticated organizer accounts.
5. The `OFFLINE` badge means a device is not currently connected to Firebase; results may not synchronize until connectivity returns. Export JSON backups regularly.

## Race-day checklist

- Finalise the registered driver list before the first stage because DNF base points depend on the registered field size.
- Confirm the stage order and DNF cutoffs.
- Configure and announce penalty names and point values before racing.
- Select the correct driver and stage on each marshal device.
- Stop the timer, review penalty taps, then press SAVE RESULT.
- Manual stopwatch results can be prepared and reviewed before saving.
- Use protected correction tools for post-save corrections and retain the correction history.

This is a custom local RC competition ruleset inspired by position-based off-road scoring; it is not an official Borneo Safari rulebook.
