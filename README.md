# Daily Dashboard — reliability update

## What changed
- Visible status states clearly that data is saved in this browser only.
- Failed saves restore the last accepted state and display an error.
- Malformed or unreadable stored data is protected from automatic overwrite.
- Saves check whether stored data changed since loading; detected conflicts require reload or an intentional restore.
- Download backup exports habits, notes, images, deadlines, subjects, sessions and board items.
- Restore validates the backup, asks before replacement, and writes before changing the visible dashboard. A failed restore leaves the existing dashboard in place.
- Image processing must finish before a note can be saved.
- Netlify configuration now publishes this static folder without an npm build.

## Deploy
Extract this ZIP. Deploy the folder containing index.html, cloud.js and netlify.toml to Netlify. For a Git deployment, use this folder as the base directory, leave the build command empty, and set the publish directory to `.`. This package does not need npm dependencies or a build step.

Keep the same deployed website address to retain access to existing browser data. A different origin has separate storage. Download a backup from the old address before moving to another address.

## Backup and restore
Open “Data & backup” and select “Download backup”. Keep that JSON file safe; it includes your notes and attached images. On another device or after a move, use “Restore backup”. Restore replaces the local dashboard only after confirmation. The maximum accepted backup file size is 20 MB; browser storage may accept less.

## Cloud sync — pending
cloud.js is the supplied, unchanged account/authentication bundle. It is not loaded because there is no account UI or dashboard storage API yet. Loading authentication alone would not back up or synchronize this dashboard.

The next step requires the existing Netlify site URL and confirmation of whether Identity or a database has already been configured. An authenticated storage backend, per-user authorization, conflict handling, and account UI must be implemented and tested before the app can claim cloud synchronization. Do not put administrator keys or database secrets in frontend code.

## Validation and remaining limits
Passed isolated JavaScript checks for syntax, all five renderers, save/reload, storage failure rollback, visible error display, invalid and valid backup restore, failed restore preservation, stale-tab detection, malformed-storage preservation, and unsafe link rejection in backups.

A real browser test was attempted but could not run because Chromium is unavailable in the execution environment. No live deployment was performed.

The previously reviewed timer-duration, midnight rollover, streak, and note-editing issues are not changed in this release. localStorage remains size-limited and does not provide transactional synchronization across tabs; avoid editing the same dashboard in multiple tabs simultaneously.
