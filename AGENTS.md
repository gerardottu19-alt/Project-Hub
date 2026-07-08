# AGENTS.md

## Cursor Cloud specific instructions

### What this repo is

This repository is a **single, self-contained, client-side web app**: `Project Hub - Vista (Standalone).html`. It is a project-management / time-tracking dashboard (projects, timers, timesheet, weekly notes, due-date calendar/Gantt with PNG export). All state persists in the browser's `localStorage`; there is **no backend, database, package manager, or build step**.

- Assets (the "Outfit" font and `html2canvas`) are inlined/bundled in the HTML, so it works fully offline.
- On load, an inline bootstrap script self-unpacks `__bundler/*` blocks into the real app, so a brief "Unpacking… / Rendering…" state may appear before the dashboard renders.

### Running it

There is nothing to build or install. Serve the file with any static server and open it in a browser:

```
python3 -m http.server 8000
```

Then open: `http://localhost:8000/Project%20Hub%20-%20Vista%20(Standalone).html`

Opening the file directly via `file://` also works since all assets are inlined; the static server just avoids `file://` edge cases and is required for headless/automated browser testing.

### Lint / test / build

- **No lint config, no test suite, and no build system exist.** Do not look for `package.json`, `Makefile`, etc.
- Verification is manual/GUI-driven: open the page, create a project, click it to start the timer, and check the Timesheet view.

### Gotchas

- The unpacker uses `DecompressionStream('gzip')`, so a reasonably modern browser is required (current Chromium/Firefox are fine).
- Because data lives in `localStorage`, state is per-browser-profile; clearing storage resets the app. Use the ⛭ settings menu's JSON export/import to back up or move data.
