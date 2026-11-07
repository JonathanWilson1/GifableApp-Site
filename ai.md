---
layout: page
title: Record GIFs from AI Coding Agents – Gifable for Mac
heading: Gifable for AI agents
lede: Let Claude Code, Cursor, Codex or any coding agent record a GIF of your Mac and drop it into a pull request.
description: Gifable's Shortcuts action lets AI coding agents record a GIF of a window, region or the whole screen from the terminal, for example to show a UI change in a pull request.
permalink: /ai/
---

## Set it up (one minute)

1. Install [Gifable](https://apps.apple.com/app/id1077840209) 4.0 or later.
2. Click the Gifable icon in the menu bar and choose **Install Shortcut for AI Agents…**, then click **Add Shortcut**.
3. Choose **Copy AI Agent Instructions** from the same menu and paste them into your agent's instructions file: `CLAUDE.md`, `AGENTS.md`, or your Cursor rules.

The first time your agent records, macOS asks you to allow Gifable under **Screen & System Audio Recording**. Recording from the menu bar never needs this permission; only the agent shortcut does, because no one is there to click the screen picker.

## Instructions for your agent

This is the text **Copy AI Agent Instructions** puts on your clipboard. If your agent can read web pages, you can also just tell it to read this page.

```markdown
## Recording GIFs with Gifable

This Mac has Gifable. To record a GIF of the screen (e.g. to show a UI change in a PR), run:

    echo "window Simulator 8" > /tmp/gifable.txt
    shortcuts run "Gifable Record" -i /tmp/gifable.txt

It records, then prints the saved file's path. Copy the file where you need it.
Requests (N = seconds, 1–60, default 5):
- `screen N`: the main display
- `window <App name> N`: that app's frontmost window, e.g. `window Simulator 8`
- `region x,y,width,height N`: points from the main display's top-left corner
Quote app names that end in a number: `window "Things 3" 5`.
On an error it prints a message saying what to fix (e.g. the window isn't on screen).
More: https://gifableapp.com/ai
```

## Good to know

- **Format and size** follow Gifable's Settings: GIF, MP4 or both, 800 pixels wide by default. Files are saved to `~/Pictures/Gifable` (or the folder you chose).
- **Windows** must be on screen and not minimised. They don't need to be in front: Gifable records the window itself, so other windows covering it don't show up.
- **Stop early** by clicking Stop in the menu bar; the agent gets the shorter clip.
- **One shortcut, one name.** If you add the shortcut twice, `shortcuts run "Gifable Record"` can't tell them apart and fails with "Couldn't find shortcut". Delete the extra copy in the Shortcuts app.
- Running the shortcut with no input (from the Shortcuts app or its menu) records the whole screen for 5 seconds.
