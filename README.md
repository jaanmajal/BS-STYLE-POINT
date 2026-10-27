# BS-STYLE POINT RC TIME ATTACK S1 v27.5.13

## Changes
- Added an Event-ID-aware Marshal Race Control link under the public results link in the organiser Firebase connection panel.
- Added a Copy marshal link button to make sharing with marshals easier.
- Marshal link format: `marshal.html?event=<EventID>`; the page preselects the Event ID from the link.
- If a shared link points to an event that does not exist online while the browser has local records, the confirmation explicitly warns and creates an empty event rather than copying another event's local driver/results data.
- Optimized `marshal.html` for mobile so Race Control, timer, start/stop/DNF/save controls and all penalty counters are compact and visible together where practical.
- Kept Manual Stopwatch Input visible below Race Control, collapsed by default.
- Existing scoring, penalty, DNF, correction and Firebase logic retained.

## Deploy
Upload all files in this folder to the root of the existing GitHub Pages repository and commit. Test on the actual phone and verify Event ID selection before using it in competition.
