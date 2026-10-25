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

- **Timer:** the length is locked once a session starts, so the minutes logged always match the session that ran. The countdown no longer finishes early, and pausing keeps the exact time left.
- **Midnight rollover:** the dashboard moves to the new day by itself, even if it was left open overnight. Habits, focus sessions and the greeting follow the real date.
- **Habit streaks:** a finished day is frozen with its own total, so adding or deleting habits later no longer changes past streaks. Deleted habits are not counted.
- **Notes:** each note can now be edited (title, subject, text, and removing attached images or links). Deleting a note asks for confirmation.

## Known follow-up work

Cloud sync between devices, Google Drive backup, and an automatic break timer are not built yet.
