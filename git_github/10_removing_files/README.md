# Removing Files

Once a file is being tracked by Git, deleting it with your file explorer or `rm` isn't enough — Git will
still see it as "deleted but not staged," and it'll keep showing up until you tell Git about the removal
explicitly.

## Removing a file completely

To remove a file from both your working directory *and* Git's tracking, use `git rm`:

```bash
git rm notes.txt
git commit -m "Remove notes.txt"
```

This does two things at once:
- Deletes the file from your working directory
- Stages the removal, so it won't reappear as an untracked file

## Removing a file from Git only (keeping it locally)

Sometimes you want the opposite: **stop tracking a file, but keep it on your machine.** This is common
when you accidentally committed something that should've been in `.gitignore` from the start — a
large log file, a `.env` with local config, or compiled build artifacts.

For this, use the `--cached` flag:

```bash
git rm --cached config.log
```

This removes `config.log` from Git's tracking and staging area, but leaves the actual file untouched
on your disk. After this, don't forget to add it to `.gitignore` so it doesn't get re-tracked by accident:

```bash
echo "config.log" >> .gitignore
git add .gitignore
git commit -m "Stop tracking config.log"
```

> **💡 Tip:** If a large or sensitive file was already committed in earlier history (not just staged),
> `git rm --cached` alone won't erase it from your repo's history — it only affects future commits.
> Removing it from history entirely requires tools like `git filter-repo` or BFG Repo-Cleaner, which is a
> more advanced topic.