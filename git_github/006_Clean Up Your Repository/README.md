A repo accumulates junk fast — a file you renamed by hand, a leftover debug file, or worse, a secret key you almost pushed to a public remote. Git gives you dedicated tools for keeping things tidy:

- `git rm <file>` — removes a file from both your working directory and Git's tracking. (Use `-cached` if you want to untrack it but keep it on disk.)
- `git mv <old> <new>` — renames a file the "Git-aware" way, instead of deleting and recreating it manually.
- `.gitignore` — a file listing patterns Git should never track (build folders, `.env` files, logs, etc.), so they never get staged by accident — even with `git add .`.

**What to do:**

- Create a throwaway file, e.g. `debug.log`, and commit it.
- Remove it properly: `git rm debug.log`, then commit the removal.
- Rename one of your existing files: `git mv notes.txt project-notes.txt`, then commit.
- Create a `.env` file with a fake secret inside, e.g. `API_KEY=12345`.
- Create a `.gitignore` file and add `.env` as a line inside it.
- Run `git status` — confirm `.env` does **not** show up as untracked (it should be ignored).
- Stage and commit the `.gitignore` file itself.
- Push everything: `git push`.
- Submit your repository link through the platform to trigger evaluation.