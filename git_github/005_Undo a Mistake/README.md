**What are `git restore` and `git revert`?**

Mistakes happen constantly when coding — and Git gives you two different tools depending on *when* you catch them:

- `git restore <file>` — undoes changes you haven't committed yet. Like hitting Ctrl+Z on a file, back to its last committed state.
- `git revert <commit>` — undoes a commit you've already made, by creating a **new** commit that reverses it. Your history stays intact; nothing gets erased.

The key idea: `restore` erases uncommitted mess, `revert` keeps the record but cancels its effect.

**What to do:**

- Modify a file but don't commit it yet.
- Run `git status` to confirm it's listed as modified.
- Run `git restore <file>` and check the file — your change is gone, back to the last commit.
- Now make a *real* mistake on purpose: change a file, `git add`, and `git commit -m "..."`.
- Run `git log` and copy the commit hash of that bad commit.
- Run `git revert <commit-hash>` to undo it. Git will open an editor for the revert commit message — save and close it.
- Run `git log` again — notice both the original bad commit **and** the new revert commit are there. Nothing was deleted.
- Push your changes: `git push`.
- Submit your repository link through the platform to trigger evaluation.