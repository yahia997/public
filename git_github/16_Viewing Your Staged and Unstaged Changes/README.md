# Viewing Your Staged and Unstaged Changes
If the git status command is too vague for you — you want to know exactly what you changed, not
just which files were changed.

To see what you’ve changed but not yet staged, type git diff with no other arguments:
```bash
git diff
```

If you want to see what you’ve staged that will go into your next commit, you can use git diff
`--staged`. This command compares your staged changes to your last commit:
```bash
git diff --staged
```