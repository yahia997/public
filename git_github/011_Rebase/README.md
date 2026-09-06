Merging isn't the only way to bring branches together. `git rebase` takes the commits from your branch and **replays** them on top of another branch's latest commit — as if you'd started your work later than you actually did. The result is a clean, linear history with no merge commits cluttering the log.

- `git rebase main` — while on your feature branch, replays your commits on top of the current tip of `main`.

Rule of thumb: rebase your own local/feature branches freely. Never rebase a branch other people are already working on — it rewrites commit history, and rewritten history breaks anyone who already pulled the old version.

**What to do:**

- Make sure `main` has moved forward since you branched off it — pull the latest, or reuse a scenario where teammates' work landed on `main` after you started (your Phase 9 setup works well here).
- Switch to your feature branch: `git checkout <feature-branch>`.
- Run `git rebase main`. If there are conflicts, resolve them the same way as Phase 9 — edit the file, remove markers, then `git add <file>` and `git rebase --continue`.
- Once it finishes, run `git log --oneline --graph` and compare it to a merge-based history — notice there's no merge commit, just a straight line.
- Push the rebased branch. Since history was rewritten, you'll need: `git push --force-with-lease`.
- Submit your repository link through the platform to trigger evaluation.