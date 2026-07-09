# Moving and Renaming Files

Unlike many other version control systems, Git doesn't explicitly track file movement or renaming.
There's no internal record that says "this file used to be called X and is now called Y." Instead, Git
detects renames *implicitly*, by comparing content — if a new file looks similar enough to a deleted
one, Git infers a rename happened when you view history or diffs.

This makes it a little surprising that Git ships with a `git mv` command at all. Here's how it works:

```bash
git mv README.md README
git status
```

## What `git mv` actually does

`git mv` is really just a shortcut. Running it is exactly equivalent to these three separate steps:

```bash
mv README.md README
git rm README.md
git add README
```

Git compares the deleted file (`README.md`) and the new file (`README`) at commit time, notices
they're nearly identical, and displays it as a rename — regardless of whether you used `git mv` or did
it manually with `mv` + `git add`/`git rm`.

## Why it matters

- **`git mv` is a convenience, not a requirement.** You can rename files with your OS, a file
  manager, or your code editor — Git doesn't care how the rename happened, only that the old file is
  gone and a similar new one is staged before you commit.
- **The "renamed" label is cosmetic.** It only shows up in `git status` and `git log --follow` output to
  make the change easier to read; Git isn't storing a rename operation anywhere internally.

> **💡 Tip:** Because Git detects renames by content similarity, renaming a file *and* heavily editing it
> in the same commit can sometimes cause Git to show it as a plain delete + add instead of a rename.
> If you want Git to reliably recognize a rename, try to keep renames and content changes in separate
> commits when possible.