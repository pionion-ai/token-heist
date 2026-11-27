# Privacy

Token Heist is a terminal. It runs on your Mac and has no server of its own.

## What it sends anywhere

Nothing. The app makes no network connections: no analytics, no crash
reports, no update checks, no account. The only time it opens the network at
all is when you choose "Open Docs" on a command, which opens a page in your
browser.

Claude Code, which you run inside it, talks to Anthropic as it always does.
That is Claude Code's behaviour and is covered by Anthropic's terms, not
changed by this app.

## What it reads

- **Claude Code's events.** The app starts Claude with an extra settings file
  of its own, which makes Claude report what it is doing (tool calls, prompts,
  cost, context use) to the window over a local socket in `/tmp`. This is
  what drives the HUD. Your own Claude settings files are never read or
  changed.
- **Keys you type at Claude's prompt.** To know which commands you use and
  whether the prompt is empty, the app follows the current input line. It is
  held in memory only and discarded when the line is sent.
- **Names and descriptions of your own commands**, from `.claude/commands`
  and `.claude/skills` in the project and your home folder, to list them.
- **What is playing** in Spotify or Apple Music (track, artist and position),
  only after you open the radio.
- **The sound your Mac is playing**, only while the Trip visualiser is on
  screen and only if you allow it. The app measures its loudness and
  frequency bands as it plays, to move the picture. No audio is recorded,
  saved or sent anywhere, and listening stops when the Trip ends.

- **Your MCP servers**, only when you open the MCP panel: the app asks Claude
  Code for its list (names, commands or addresses, status) and shows it. The
  list is not saved. Adding or removing a server there runs Claude Code's own
  command; what you type, including any keys, goes to Claude Code and is not
  kept by this app.

## What it keeps on your Mac

In `~/Library/Application Support/Sundown/`:

| File | Holds |
|---|---|
| `loadouts.json` | The model, effort and permission choices last used per folder |
| `stash.json` | Which commands you have used and how often, pins, tip history |
| `soundtrack.json` | Per-song totals: lines written, cost, tool calls, time played |
| `stations.json` | Spotify links you saved as radio stations |
| `claude-settings.json` | The settings file handed to Claude Code |

Recent folders, font and window choices are in the app's preferences. Delete
the folder and the preferences to remove everything; nothing else is stored.

## Permissions macOS may ask for

- **Microphone:** used by Claude Code's own voice mode. The app itself
  records nothing.
- **System audio recording:** used by the Trip to follow the music. That is
  macOS's name for the permission; the app analyses the sound and keeps none
  of it. Decline and the Trip runs on its own clock.
- **Automation (Spotify, Music):** used by the radio to play, pause, skip,
  seek and read the current track.
- **Desktop, Documents, Downloads:** needed by any terminal that runs
  commands in those folders.
