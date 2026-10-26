# BS-STYLE POINT RC TIME ATTACK — S1 v15

## Scoring and DNF gate progress

- Finishing order is determined by raw elapsed time (fastest first). Penalty deductions do not add time and do not change raw-time order.
- Base position points: 1st 100, 2nd 95, 3rd 90, 4th 87, 5th 84, 6th 81, 7th 78, 8th 75, 9th 72, 10th 69; the published scale continues through 40th, and 40th or lower receives 26 base points.
- Dynamic DNF base = `max(20, points for the last registered position - 20)`.
- Each Special Stage has an editable total gate-marker count in Section 1. Set it before racing; once any result is saved for that stage, the total gate count cannot be changed. New stages default to 10 gates.
- DNF must have a gate-progress count before SAVE RESULT can be pressed. The marshal enters gates cleared from 0 to the stage total after pressing DNF or after timeout.
- DNF progress base = `round(dynamic DNF base * gates cleared / total gates)`. Then subtract that driver's point penalties; minimum 0. A legacy DNF result without gate-progress data retains the old full DNF base until corrected.
- FINISH net points = `max(dynamic DNF base, position base points - penalty point deductions)`. Thus, a FINISH result never scores below the full DNF base for the current field.
- DNS = 0 points. Net stage score cannot be below 0 for DNF.
- Default shared penalty types: Touch = 15 points per tap; Gate violation = 5 points per tap; Roll-over = 5 points per tap. Organisers can edit the shared penalty rules before racing in Section 5. Each tap snapshots the value at the time of the tap. Do not penalise the same incident with both time addition and point deduction.
- Overall champion: highest accumulated net points. Ties are resolved by more FINISH stage results, then net points in the final SS, then more recorded stages, then lower cumulative raw time, then lower race number.

## Race-day workflow

1. Finalise the registered driver list before SS1 because dynamic DNF base points depend on field size.
2. For each SS, unlock admin, set DNF cutoff and total gate markers, then save settings before the first run. Gate totals lock after the first saved result in that SS.
3. Configure and announce penalty types and point values before racing.
4. Select the correct SS and driver on the marshal device. Check the OFFLINE/ONLINE indicator.
5. For FINISH, stop the timer, review penalties, then SAVE RESULT.
6. For DNF or timeout, enter gates cleared in the DNF progress panel, review the estimated points and penalty taps, then SAVE RESULT. The save button remains disabled until the gate count is valid.
7. Manual stopwatch input can prepare or override a pending result before saving. If the manual status is DNF, gate progress is still required.
8. Use protected correction tools for post-save corrections. DNF corrections also require a gate count. Retain correction history and export JSON backups regularly.

## Publishing / Firebase

1. Upload `index.html`, `results.html`, `firebase-config.js`, `logo.jpg`, and `README.md` to the root of the GitHub repository.
2. GitHub Pages: Settings → Pages → Deploy from a branch → `main` → `/(root)`.
3. Default Event ID: `bs1`. Use the same Firebase project and Event ID on every timing device. Organizer email/password are entered at connect time and are not persisted by the app.
4. Configure Firebase Realtime Database rules carefully. Do not use public write access.
5. `OFFLINE` means a device is not currently connected to Firebase; results may not synchronize until connectivity returns. Export JSON backups regularly.

This is a custom local RC competition ruleset inspired by position-based off-road scoring; it is not an official Borneo Safari rulebook.
