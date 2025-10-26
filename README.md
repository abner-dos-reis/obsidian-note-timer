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

Installing GitHub CLI (`gh`) without sudo (Flatpak environment / no root permissions)
-------------------------------------------------------------------------------------

The steps below download the `gh` binary for Linux (amd64) and place it in `~/.local/bin` — no sudo required.

Copy and run in your terminal (your shell is `sh`):

```sh
mkdir -p "$HOME/.local/bin"
cd /tmp
url=$(curl -s https://api.github.com/repos/cli/cli/releases/latest | grep 'browser_download_url' | grep 'linux_amd64.tar.gz' | head -n1 | cut -d '"' -f4)
echo "Downloading $url"
curl -L "$url" -o gh.tar.gz
tar -xzf gh.tar.gz
mv gh_*_linux_amd64/bin/gh "$HOME/.local/bin/"
chmod +x "$HOME/.local/bin/gh"
"$HOME/.local/bin/gh" --version
```

Authentication and Repository Creation (authorize via browser)
--------------------------------------------------------------

After installing `gh`, run within the project folder:

```sh
cd /path/to/obsidian-note-timer
gh auth login --web
# follow browser instructions to authorize
gh repo create REPO_NAME --public --source=. --remote=origin --confirm --push
```

Note: `gh repo create` will use your authenticated GitHub account and create a public repository. Replace `REPO_NAME` with your desired name (e.g., `obsidian-note-timer`).

What Was Done Here
------------------

- Read the project files and summarized functionality.
- Added this `README.md` with usage instructions, installation, and how to install `gh` without sudo.

Suggested Next Steps
--------------------

- (Optional) Include the non-bundled source code (original TypeScript/JS) to facilitate maintenance.
- Add LICENSE/NOTICE if you want to redistribute (check the upstream license).
- Test the `gh auth` and `gh repo create` workflow in the user environment to confirm permissions.

-- End
