# Daily Dashboard

[Open the dashboard](https://hardiksucksatai.github.io/App-1/)

A personal study dashboard with daily habits, a focus timer, a task board, notes, deadlines, flashcards, and quizzes.

## Hosting on GitHub Pages

The app is a static website. Its HTML, styles, JavaScript, and built-in study material are contained in `index.html`. No package installation, build command, or server is required.

In this repository, open **Settings → Pages** and use:
- Source: **Deploy from a branch**
- Branch: **main**
- Folder: **/ (root)**

Commit updates to `main` to publish them through GitHub Pages. Check the **Actions** tab for deployment progress.

## Data and backups

Built-in study material is part of the website. Personal changes, notes, images, habits, tasks, deadlines, and progress are saved in the current browser using localStorage. They are not committed to GitHub or automatically shared between devices.

Open **Data & backup** to download a JSON backup or restore one. Restore validates the file and asks before replacing the current dashboard. Keep backup files outside this public repository.

A new website address uses different browser storage. Download a backup before moving between addresses or clearing browser data.

The app reports failed saves, restores the last accepted state after a failed save, protects unreadable stored data from automatic overwrite, and detects changes made by another tab before saving. Browser storage remains size-limited; avoid editing in several tabs at once.

## Google Drive

The existing Drive folder and document links open study resources. Google Drive backup and synchronization are not connected yet.

## Project files

- `index.html`: dashboard and built-in study material.
- `README.md`: setup and usage instructions.

The unused Netlify deployment configuration and authentication bundle have been removed. This repository has no Netlify dependency. Removing those files does not delete or disable the separately hosted old site.

## Recent fixes

- **Note drafts:** new notes and inline edits survive switching tabs and refreshing the same browser tab. Drafts use session storage; use **Save note** or **Save changes** to keep them after closing the tab. Storage failures are reported without clearing the in-memory draft.
- **Timer:** subject and duration stay fixed once a focus session starts, including while paused. Running and paused sessions survive refreshes. Completion and study-minute credit are saved together with a session ID to prevent duplicate credit on reload. Failed completion saves can be retried.
- **Midnight rollover:** the dashboard updates the date, habits, study totals, and deadline labels when the day changes. Focus sessions count on their completion date.
- **Habit streaks:** daily habit-ID snapshots preserve completed-day history when habits are added or removed. Existing frozen totals are retained. Older records without snapshots or totals use the active habit list once during migration; exact historical totals cannot be reconstructed.
- **Notes:** edit a note inline, preserve or remove its attachments, and add new attachments or links. Deletion asks for confirmation and moves notes into **Deleted notes**, where they can be restored. Deleted notes are excluded from quizzes and included in backups.
- **Quizzes:** multiple-choice alternatives come from the same note/chapter as the question. Chapters without three distinct wrong answers use flashcards instead of unrelated options.

Older dashboard data, frozen streak totals, and the earlier independent timer format are migrated automatically. Restoring a backup pauses its timer rather than starting a countdown from another device.

## Validation

The reliability update passed 15 DOM-based regression scenarios covering drafts and edits, storage failures, deletion and restore, timer refresh/pause/completion, legacy migration, midnight rollover, streak history, quiz options, backup validation, and stale-tab protection.

## Known follow-up work

Cloud sync between devices, Google Drive backup, and an automatic break timer are not built yet. Breaks start manually. Quiz alternatives are chapter-based; their educational quality and the built-in answers still need a separate content review.
