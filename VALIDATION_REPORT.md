# v27.6.0 Dry-Run Package - Validation Report

## Automated checks passed

- `index.html`: 1 inline JavaScript block passed `node --check`.
- `marshal.html`: 2 inline JavaScript blocks passed `node --check`.
- `results.html`: 1 inline JavaScript block passed `node --check`.
- `firebase-config.js` passed `node --check`.
- `firebase-locking-rules.json` parsed as valid JSON.
- `RULES_SCORING_v2.pdf` generated with ReportLab and checked as a 3-page PDF.
- HTML parser found no duplicate static element IDs:
  - organiser: 118 IDs
  - marshal: 115 IDs
  - public results: 28 IDs
- Scoring-function tests passed for:
  - DNF at zero gates = 0 points
  - partial and full gate-progress DNF calculations
  - FINISH Gate-1 minimum floor
  - DNS = 0 points
  - FINISH above DNF above DNS on equal points

## Not yet verified

- Firebase Realtime Database rules have not been deployed or tested in the Firebase Emulator.
- The package has not been tested against the live Firebase project.
- Two-phone stage-lock contention, access revocation, offline queue recovery and iOS Safari timing still require a real-device dry run.
- GitHub Pages deployment and cache refresh have not been tested.

## Release state

Prepared as a separate package only. No files were pushed to GitHub, no Firebase rules were changed, and the current live website/database remain untouched.
