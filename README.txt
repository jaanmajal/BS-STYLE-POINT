BS-STYLE POINT RC TIME ATTACK v27.7.8
SAFE MARSHAL RESULT UPLOAD RECOVERY FOR EVENT bs1 / OTHER EVENTS

WHY THIS UPDATE
A queued marshal result can receive PERMISSION_DENIED when its previous
stage lock was replaced by an organiser-authorised takeover. Firebase
Rules v7 allow normal result writes only while that original run holds
the matching stage/session lock. Relaxing this rule would risk overwriting
competition results. The new solution provides a separate, controlled
organiser recovery inbox.

FILES
- index.html: Main Control (with new Marshal Recovery Inbox panel)
- marshal.html: Marshal (with SEND QUEUED RESULT FOR ORGANISER REVIEW)
- firebase_rules_v8.json: COMPLETE Firebase Realtime Database rules
- firebase_rules_v8_copy_paste.txt: identical rules to copy and paste

INSTALLATION — DO IN THIS ORDER
1. Keep the affected marshal phone/browser and queued local result.
   Tap Export backup on that same device and save the JSON backup.
   DO NOT clear browsing data, reset event, sign out, or delete queue.
2. Firebase Console > Realtime Database > Rules: BACK UP existing rules,
   paste the COMPLETE firebase_rules_v8.json content and click Publish.
   Rules v8 preserve the original Rules v7; they add an organiser-only
   recovery inbox and an immutable submit privilege for the active marshal.
3. Replace index.html AND marshal.html in the existing GitHub Pages
   repository, maintaining the original names. Do not upload the Rules
   file to GitHub.
4. Refresh BOTH Main Control and Marshal (same original web origin).
   If the marshal link is closed, reopen it at Main Control first.
5. On affected marshal phone: Connect to event bs1 and confirm ONLINE.
   Use SEND QUEUED RESULT FOR ORGANISER REVIEW and confirm.
   The original queue is retained until the official result is verified.
6. On Main Control, sign in as the organiser, expand
   'Marshal Recovery Inbox (organiser review)' and click LOAD.
   Review the driver, SS, recorded time and penalties. Ensure no vehicle
   is currently running on the affected stage. Press REVIEW & IMPORT.
   It refuses to overwrite an existing different result or import while
   the stage has a running lock.
7. On the marshal phone, press RETRY PENDING SYNC. If Firebase's official
   result is identical to the queued value, the old queue entry is
   cleared without rewriting that official result.

IMPORTANT
* If there is a different official result or existing penalty values,
  the ticket stays for organiser review; do not force overwrite.
* The new inbox is NOT a public result. It becomes official only when
  the organiser approves it in Main Control.
* Replacing the HTML does not intentionally remove localStorage on
  the original browser origin, but back up before deployment.
* The site and Firebase Rules must be deployed before live recovery.
* Real Firebase authorization/deployment has NOT been tested. JS and
  browser simulation tests have passed.
* Previous stage reset PIN 123456, manual timer START after takeover,
  next-driver display, any eligible driver selection, empty manual
  stopwatch field, and existing scoring have been retained.

ERROR PATH EXAMPLE
Event: bs1
Result path: results/dmvp7e116p2llk/4
This means Special Stage SS5 (zero-based index 4).

TEC-ARTS CRAWLER
