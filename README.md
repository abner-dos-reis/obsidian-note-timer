README
======

Obsidian Note Timer (Adaptation)
---------------------------------

This project is a local adaptation of the "obsidian-note-timer" plugin by davidvdev.
Original source: https://github.com/davidvdev/obsidian-note-timer

Overview
--------

This plugin adds an embedded timer to Markdown code blocks using the timer language.
It displays buttons to start, stop, and (optionally) reset the timer, with the log feature removed.

Main Files
----------

- `main.js` — generated/bundled file with the plugin logic (timer code block processor, settings persistence, log creation, etc.).
- `manifest.json` — plugin metadata (id, version, author, etc.).
- `styles.css` — minimal styles for the timer block presentation.

Features
--------

- Adds a code block processor for ```` ```timer ````
- Generates a UID for each `timer` block and maintains state (running/stopped) in memory during the session.

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

Local Installation (Manual)
---------------------------

1. Copy this project folder to the Obsidian plugins directory (e.g., `.obsidian/plugins/obsidian-note-timer`).
2. Restart Obsidian (or reload plugins) and enable "Note Timer" in community settings.

License / Attribution Notes
---------------------------

This repository is a local adaptation of davidvdev's work. The code in `main.js` is the generated bundle version (the original `source` is in the upstream project). Please preserve attribution to the original author and check the upstream license before redistributing.
