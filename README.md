# BS-STYLE POINT RC TIME ATTACK — Marshal-only link (v27.5.12)

This package adds `marshal.html`, a dedicated mobile-friendly marshal URL that displays only Section 1 Race Control while retaining the same application logic and Firebase configuration.

## GitHub Pages URL
After uploading all files to the existing repository root, use:

`https://jaanmajal.github.io/BS-STYLE-POINT/marshal.html`

## How it works
- `marshal.html` is a focused view of the same Race Control app.
- The other sections are hidden from the marshal page; their DOM remains available to the existing app logic.
- The connection/Event ID controls are available in a compact, collapsible panel.
- Uses the same `firebase-config.js`, Event ID field, local storage keys and Firebase event data as `index.html`.
- `index.html` remains the full organiser/admin interface.
- `results.html` remains the public results page.

## Deployment
Upload/replace the included files in the repository root and commit. Do not delete `index.html` or `results.html`.

## Important
The marshal-only view is a user-interface convenience, not a security boundary. Admin permissions and Firebase security rules still need to protect privileged operations. Test sign-in, timer start/stop, saving a result, and syncing on two devices before competition.
