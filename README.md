# BS-STYLE POINT RC TIME ATTACK S1 v27.5.2 — Late-entry sync fix

This hotfix is based on the preferred v27.5.1 interface and retains the favicon and collapsible Clear All Race Data section.

## Fix
- When a queued `lateEntries/<driverId>` record conflicts with Firebase, the app checks whether both records refer to the same registered driver and same target SS.
- If they match, it merges the position metadata and retries the upload without asking the organiser to overwrite the whole record.
- If the driver or target SS differs, the existing conflict confirmation remains; no unrelated conflict is silently overwritten.

## Retained
- Existing Firebase project and Event ID workflow
- Driver Draw & Spin, late driver entry, driver name editing
- Scoring, penalties, DNF gate progress, correction workflow
- Local safety snapshots and persistent sync queue
- Browser favicon using the TEC-ARTS CRAWLER logo
- Collapsible Clear All Race Data section and reset password workflow

## Deploy
Replace the repository files with this package and commit. Test late-entry creation and pending-sync recovery on the same Event ID before competition. This package has not been verified against the live Firebase project.
