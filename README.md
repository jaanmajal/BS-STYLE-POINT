# BS-STYLE POINT RC TIME ATTACK S1 v8 — Editable Event ID

This is a separate S1 version based on the uploaded RC Time Attack V12 Spacebar Edition. It keeps the multi-stage timer, Spacebar start/stop, automatic DNF cutoff, admin PIN protection, online Firebase sync, correction history, backups and public results page, while changing the overall leaderboard to position points.

## Files
- `index.html` — organizer/race-control interface
- `results.html` — public read-only live points leaderboard
- `firebase-config.js` — shared Firebase project config and event ID
- `logo.jpg` — TECH-ARTS CRAWLER logo

## Scoring
- Finishers are ranked in each SS by adjusted time: raw time + assigned time penalties.
- Position points: 1st 100, 2nd 95, 3rd 90, 4th 87, 5th 84, 6th 81, 7th 78, 8th 75, 9th 72, 10th 69, 11th 66, 12th 63, 13th 60, 14th 58, 15th 56, 16th 54, 17th 52, 18th 50, 19th 48, 20th 46, 21st 45, then 44 down to 26 at 40th; 40th and later receive 26.
- DNF = 20 points. DNS = 0 points.
- Overall ranking: highest total points, then points in the final SS, then number of recorded stages, then lower total adjusted time.
- Positive penalty seconds add time; negative seconds reduce time. Penalty types and values are configured once in a shared list used by every stage. Editing a shared rule updates matching applied penalty entries across all stages; removing a rule does not delete already applied penalties.

## 1. Firebase project configuration (already filled in)
This S1 v8 package is preconfigured for the Firebase Web App you created:
- Firebase project ID: `bs-style-point`
- Realtime Database URL: `https://bs-style-point-default-rtdb.asia-southeast1.firebasedatabase.app`
- Default Event ID: `rc-points-s1`
- Firebase Web App values are permanently stored in `firebase-config.js`; API key, auth domain, database URL and project ID fields in Race Control are read-only. Only Event ID, organizer email and password remain editable. The Event ID can be edited in Race Control and is saved in that device browser only. All timing devices must use the exact same Event ID. The public results page accepts an Event ID in its URL, for example `results.html?event=rc-points-s1`.

Do not type or replace the project configuration on each device. Firebase project configuration fields in Race Control are read-only. The Event ID is editable; disconnect first before changing it, and reconnect afterward. Enter the authorized organizer email and password only when signing in. The app does not persist these credentials in its own local configuration. Keep the organizer password private. If you intentionally create a different Firebase project later, update `firebase-config.js` and republish all files.

Firebase Web App config is browser-visible by design; it is not an admin secret. Security depends on Authentication and Realtime Database rules.

## 2. Realtime Database rules (configure in Firebase Console)
The public results page needs read access, while writing should require an authenticated organizer. A simple event-level rule is:
```json
{
  "rules": {
    "events": {
      "$event": {
        ".read": true,
        ".write": "auth != null"
      }
    }
  }
}
```
This makes event results publicly readable. Only create trusted organizer accounts because any authenticated account permitted by these simple rules can write to events. For stronger production security, use role-based rules/custom claims or a backend.

## 3. Publish to a NEW GitHub repository
1. Create a new repository, for example `rc-crawler-points-s1`.
2. Upload `index.html`, `results.html`, `firebase-config.js`, `logo.jpg`, and this README to the repository root.
3. Open Settings > Pages. Choose Deploy from a branch, branch `main`, folder `/ (root)`, then Save.
4. After GitHub Pages deploys, your organizer page will be `https://YOUR-USERNAME.github.io/rc-crawler-points-s1/` and public results will be `https://YOUR-USERNAME.github.io/rc-crawler-points-s1/results.html`.

## 4. Connect race-control devices
1. Open the organizer page on each timing device.
2. Select Online sync setup. The config fields are prefilled from `firebase-config.js`; enter the organizer email/password and tap Connect.
3. Set the same Event ID on every timing device. The ID is editable in Online sync setup and is saved in each device browser. If you change the ID, disconnect first and reconnect using the new ID on every device.
4. For the first device, approve creating the event from the local roster if asked. Other devices should load the existing online event.
5. Share the `results.html?event=YOUR_EVENT_ID` URL with spectators (replace `YOUR_EVENT_ID` with the exact Event ID used by Race Control). They do not need to sign in, but Firebase rules must permit public read access.

## 5. Penalties
1. Before the race, unlock protected changes with the admin PIN (`123456` inherited from the source version).
2. Scroll below the live leaderboard to **Shared time penalty setup**. Add each penalty type once with its time value. The same list appears for every SS. Use positive seconds to add time and negative seconds to reduce time.
3. During racing, use the quick penalty buttons inside the timer section. Each tap records exactly one occurrence for the active timer driver (if a timer is running) or the selected driver, for the active SS. No PIN or confirmation is required for this quick action.
4. Each tap is saved to the result data and added to the local correction/audit history. The adjusted time, stage points and overall points recalculate automatically.
5. Edit a shared rule by changing its name/value and tapping Save. Remove a rule with Remove; previously recorded penalties remain attached to drivers. To remove an applied occurrence, unlock admin controls and use the applied-penalties table below the shared rules.
6. A time penalty does not itself convert a finisher to DNF; the DNF cutoff is based on the actual timed run.

## Notes
- S1 uses separate browser storage keys from the original V12 app and a separate default Event ID. The original files are not modified.
- Admin PIN remains `123456` from the original source; change it in `index.html` before a public event if desired.
- Export JSON backups regularly. Keep race-control tabs visible and prevent devices from sleeping during timing.


## Penalty tap counter (S1 update)

- Configure the shared penalty type list and time values in Section 5. This section stays in its existing location and requires the admin PIN.
- Under the timer, each configured type has an Add 1 action and a Remove 1 action, plus a tap count and accumulated time adjustment for the selected driver and stage.
- Each add/remove tap is saved and added to the correction history. These counter actions do not require the admin PIN.
- The counter shows one row/card per penalty type rather than a long repeated row for every tap. The total tap count and total time adjustment are shown below the counters.
- Removing a type from Section 5 does not erase penalties already applied; those remain visible as a removed rule and can still be reduced one tap at a time.


## S1 v4 race-control workflow

- The stopwatch has an OFFLINE/ONLINE badge beside the time. OFFLINE means the device is not currently connected to Firebase; check this before racing because local-only changes will not appear on other devices until synchronized.
- The driver registration section is below the leaderboard. Section 5 (shared penalty setup) remains directly below the leaderboard and is still protected by the admin PIN.
- Section 3, Manual stopwatch input, is collapsible. Use it when timing with a separate stopwatch; prepare a result first, review penalty counts under the timer, then tap SAVE RESULT.
- STOP only freezes the timer. It does not save the result. Review the penalties, then press SAVE RESULT. Automatic or manual DNF also waits for SAVE RESULT.
- A pending result is kept locally if the page is refreshed. After a result is saved, its penalty counters are locked; select the next driver to reset the stopwatch display.
- Manual result statuses available are Finish, DNF, and DNS. Finish time must be entered as mm:ss.cc and be below the stage cutoff.


## S1 v5 leaderboard status

- The leaderboard Status column displays only `FINISH` or `PENDING`.
- `FINISH` means the driver has a recorded result for every configured SS. A recorded stage result may be Finish, DNF, or DNS.
- `PENDING` means at least one configured SS has no recorded result yet. Individual SS cells still show their own Finish time, DNF, or DNS result.


## S1 v8 editable Event ID
- Firebase Web App settings remain embedded in `firebase-config.js`. The default Event ID is `rc-points-s1`.
- Race Control allows the Event ID to be edited and saves it in local browser storage. The same ID must be entered on every timing device. Disconnect before changing the ID while online, then reconnect.
- Public Results reads `?event=EVENT_ID` from its URL and uses that event path; share the matching URL with spectators.
- Organizer email and password remain blank until entered for sign-in and are not saved by the app.
- The Firebase project has a Realtime Database in Singapore (`asia-southeast1`) and Email/Password sign-in enabled. Before online testing, confirm the database rules are set as intended and add the deployed GitHub Pages host under Authentication > Settings > Authorized domains if needed.
