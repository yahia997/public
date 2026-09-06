Sometimes you're deep in unfinished work when something urgent comes in — a critical bug that needs fixing *right now*, on a different branch. You can't commit half-finished work, but you also can't lose it. This is exactly what these two commands are for:

- `git stash` — temporarily shelves your uncommitted changes and gives you a clean working directory. `git stash pop` brings them back later.
- `git cherry-pick <commit-hash>` — takes one specific commit from anywhere in the repo and applies it onto your current branch, without needing a full merge.

**What to do:**

- On your feature branch, make an uncommitted change to a file — don't commit it.
- Run `git stash` — check `git status`, your change is gone, working directory is clean.
- Switch to `main`: `git checkout main`, then create a hotfix branch: `git checkout -b hotfix/urgent-fix`.
- Make a small, clearly-labeled fix (e.g. correct a typo in `README.md`), commit it.
- Find that commit's hash with `git log`, then imagine you need it on a different branch too: `git checkout <some-other-branch>` and run `git cherry-pick <commit-hash>`.
- Push the hotfix branch: `git push -u origin hotfix/urgent-fix`.
- Return to your original feature branch: `git checkout <feature-branch>`.
- Bring your shelved work back: `git stash pop`. Confirm your uncommitted change is exactly as you left it.
- Submit your repository link through the platform to trigger evaluation.