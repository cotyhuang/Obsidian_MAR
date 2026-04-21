---
tags: [Git, VSCode, VersionControl]
aliases: [Git Status Meanings, VSCode Explorer Icons]
---

# Git Status Icons in VSCode

The icons you've highlighted in the **VSCode Explorer** are indicators from the built-in **Git source control** integration. They tell you the current state of your files relative to your last commit.

## Breakdown of Status Indicators

| Icon | Meaning | Description |
| :--- | :--- | :--- |
| **U** | **Untracked** | The file is new and has not been added to the Git repository yet. |
| **M** | **Modified** | The file exists in your last commit, but you have made changes to it that aren't saved to the repo yet. |
| **●** (Solid Circle) | **Staged** | The changes (new or modified) have been "added" (staged) and are ready to be included in your next commit. |
| **A** | **Added** | Specifically used for new files that have been staged for the first time. |

> [!tip] Quick Tip
> In your screenshot, most of your **FRB SA** and **Basel** notes are marked with **U**, meaning they are new files. The **INDEX.md** is marked with **M**, meaning you've updated your index but haven't committed those changes yet.

## What should you do?
If you want to save these changes to your version history:
1. Open the **Source Control** tab (shortcut: `Ctrl+Shift+G`).
2. Click the **+** icon next to the files to "Stage" them (this turns **U** or **M** into the **●** icon).
3. Type a message in the box and click **Commit**.

#Tags
#Git #VSCode #Obsidian #Workflow