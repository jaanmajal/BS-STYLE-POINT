BS-STYLE POINT RC TIME ATTACK - UPDATE v27.6.8
Based on Borneo RC Safari BS Solo v27.6.7 package, preserving its scoring,
penalty values, race data paths, marshal stage locks and existing Firebase config.

UPDATE 1 - MARSHAL PHONE STAGE UNLOCK
- On the existing Stage Already In Use popup, the admin can enter the
  SAME existing organiser/admin PIN (unchanged) directly on the marshal phone.
  PIN is validated by the updated Firebase Database Rules (v4) on the server.
- The system rechecks the exact stage lock in Firebase. It first attempts safe
  auto-release if the saved result is verified. Otherwise it requires TWO
  explicit confirmations that the old run has stopped and is no longer active.
- Unlock is a transaction that removes ONLY the matching lock, then verifies
  Firebase and automatically retries claiming the stage.
- Firebase connection and marshal access must still work. A forbidden Firebase
  transaction fails safely rather than claiming success.
- The PIN is never cached on the marshal phone or hardcoded in public HTML.
- Important: 6-digit PINs are still guessable. Use a stronger backend-auth scheme
  for higher-security races; a Firebase Rules check is not rate-limited.

UPDATE 2 - MAIN CONTROL EDITS WITHOUT ADMIN PIN
- Removed the Protected Changes PIN panel and the PIN requirement for edits.
- Existing race-safety checks (no editing the exact active/pending result,
  limits during running, confirmations) remain.
- Existing Firebase organiser sign-in remains required for remote organiser
  actions; Prepare New Race and Clear All Race Data use their independent
  passwords and are NOT made passwordless.

UPDATE 3 - ANDROID RESULT SCROLL
- Make viewport handle vertical swiping; remove a nested pending-list scroll trap.
- Allow normal Android vertical scroll through the mobile driver cards and
  expanded stage chips; desktop detail table retains horizontal scrolling.
- Preserve mobile card layout and existing filters/leaderboard.

PUBLISHING
1. Back up the CURRENT Firebase Rules and existing deployed files first.
2. In Firebase Console > Realtime Database > Rules, paste and PUBLISH the
   supplied BS_STYLE_POINT_firebase_rules_v4_STAGE_OVERRIDE.json (separate file).
   This keeps the prior v3 read/write permissions and adds an admin-PIN reset ticket.
   Do NOT upload this rules JSON to the public GitHub Pages repository.
3. Replace index.html, marshal.html and results.html in repository root.
4. Leave firebase-config.js, logo.jpg, favicon.png and Firebase data unchanged.
5. Verify refresh with browser cache bypass on Android.
6. Test a stuck SS stage on a fresh test Event ID before a real race.

TEST CASES
A. Main Control: add/edit driver, stage cutoff, draw and correction without PIN.
B. Prepare New Race / Clear All Race Data: still asks its OWN password.
C. Marshal: incorrect PIN must be rejected by Firebase, correct PIN
   opens confirmations; changed or other-stage runs must not be cleared.
D. A live/unsaved run: refuse reset unless organiser has physically checked
   the track and accepted two warnings.
E. Android Results: vertically scroll the pending driver lists, open the
   mobile card Stage Details sections, and scroll up/down from cards and
   buttons. Check Chrome and Android WebView on a real device.

The attached v2.1 rules PDF has not been modified in this patch.
