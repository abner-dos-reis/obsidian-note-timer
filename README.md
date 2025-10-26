README
======

Obsidian Note Timer (Adaptation)
---------------------------------

This project is a local adaptation of the "obsidian-note-timer" plugin by davidvdev.
Original source: https://github.com/davidvdev/obsidian-note-timer

Overview
--------

This plugin adds an embedded timer to Markdown code blocks using the `timer` language.
It displays buttons to start, stop, and (optionally) reset the timer, and can maintain a log
in table format within the Markdown file itself.

Main Files
----------

- `main.js` — generated/bundled file with the plugin logic (timer code block processor, settings persistence, log creation, etc.).
- `manifest.json` — plugin metadata (id, version, author, etc.).
- `styles.css` — minimal styles for the timer block presentation.

Features
--------

- Adds a code block processor for ```` ```timer ````
- Generates a UID for each `timer` block and maintains state (running/stopped) in memory during the session.
- Supports configuration via the `timer` block (e.g., customize button texts, control whether milliseconds are displayed, etc.) and via the plugin settings tab.
- When enabled, creates a log table below the timer block with columns: Start | Stop | Duration | Comments and updates the Total Time.

How to Use
----------

1. Install the plugin (see instructions below).
2. In your Markdown file, add a code block with the `timer` language:

```
```timer
_timerUID:optional-id
ms: true
```

3. When rendering the note, the block will display the time and Start/Stop/Reset buttons according to configuration.
4. If `autoLog` is enabled (in plugin settings), when stopping the timer the time will be added to the log table.

Supported settings (visible in generated code / via plugin settings):

- autoLog: automatically adds log to the table
- dateFormat: date format in the log (e.g., YYYY-MM-DD)
- logDateLinking: `none` | `tag` | `link` — how the plugin formats dates in the log
- msDisplay: show milliseconds
- startButtonText / stopButtonText / resetButtonText
- showResetButton / continueRunningOnReset

Local Installation (Manual)
---------------------------

1. Copy this project folder to the Obsidian plugins directory (e.g., `.obsidian/plugins/obsidian-note-timer`).
2. Restart Obsidian (or reload plugins) and enable "Note Timer" in community settings.

License / Attribution Notes
---------------------------

This repository is a local adaptation of davidvdev's work. The code in `main.js` is the generated bundle version (the original `source` is in the upstream project). Please preserve attribution to the original author and check the upstream license before redistributing.
