Up until now, everything has happened on a single branch (`main`). But real projects never work that way — nobody edits the "official" version of the code directly. Instead, every new piece of work gets its own **branch**: an isolated copy of the codebase where you can experiment, break things, and commit freely without affecting anyone else.

- `git branch <name>` — creates a new branch.
- `git checkout <branch>` (or `git checkout -b <name>` to create and switch in one step) — switches your working directory to that branch.

Good branch names describe the work: `feature/user-login`, `bugfix/null-pointer`, `docs/update-readme`.

**What to do:**

- Make sure you're on `main` and it's up to date: `git checkout main`.
- Create and switch to a new branch: `git checkout -b feature/my-first-branch`.
- Confirm you're on it: `git status` should show your branch name.
- Create or modify a file — something clearly new, like `feature.txt`.
- Stage and commit it: `git add feature.txt`, `git commit -m "..."`.
- Push the branch (not `main`!): `git push -u origin feature/my-first-branch`.
- Switch back to `main`: `git checkout main` and confirm your new file is **not** there — it only exists on the branch.
- Submit your repository link through the platform to trigger evaluation.