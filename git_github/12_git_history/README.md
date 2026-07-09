# Viewing the Commit History

After you've created several commits, or if you've cloned a repository with an existing commit
history, you'll probably want to look back and see what has happened. The most basic and powerful
tool for this is the `git log` command.

## Basic usage

```bash
git log
```

By default, each entry shows:
- The commit's **SHA-1 checksum** — a unique ID for that commit
- The **author's name and email**
- The **date** the commit was made
- The **commit message**

## Useful flags

`git log` becomes far more practical once you start combining it with a few key flags:

| Flag | What it does |
|---|---|
| `-p` or `--patch` | Shows the actual diff (line-by-line changes) introduced in each commit |
| `-<n>` (e.g. `-3`) | Limits output to the last *n* commits |
| `--stat` | Shows a summary of files changed and how many lines were added/removed per commit |
| `--oneline` | Condenses each commit to a single line (short SHA + message) — great for a quick overview |
| `--graph` | Draws an ASCII graph of branch and merge history alongside the log |
| `--author="name"` | Filters commits to only those made by a specific author |
| `--since=` / `--until=` | Filters commits within a date range (e.g. `--since="2 weeks ago"`) |
| `--grep="text"` | Filters commits whose message contains the given text |

## Combining flags

Flags can be combined to build a much more readable history view. A very common one:

```bash
git log --oneline --graph --all
```

This compact view is often more useful day-to-day than the full default output — you get a fast
overview of what happened and how branches relate, without scrolling through walls of text.

> **💡 Tip:** If you only care about the history of a *specific file*, run `git log -- path/to/file` to see
> only commits that touched that file.