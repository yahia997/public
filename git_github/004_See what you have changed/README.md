Before you save or share anything, it helps to actually *see* what's going on. Git gives you three windows into your project's current state:

- `git status` — tells you which files are staged, modified, or untracked right now.
- `git diff` — shows you the exact lines that changed before you commit them.
- `git log` — shows the full history of commits you've already made.

Think of these as your dashboard — you'll run them constantly, often several times per minute, without even thinking about it.

**What to do:**

- Modify one of your existing files (e.g. `notes.txt`) — add a line, change a sentence, anything.
- Run `git status` and notice how the file is now listed as **modified**.
- Run `git diff` and read the output — lines starting with (-) are what's being removed, lines starting with `+` are what's being added.
- Stage the file with `git add <file>`, then run `git status` again — notice how it moves from "Changes not staged" to "Changes to be committed."
- Run `git diff --staged` and compare it to the plain `git diff` from before.
- Commit the change, then run `git log` to see it appear at the top of your history.
- Try `git log --oneline` for a shorter, one-line-per-commit view.

**Submission:** None — this phase is about building the habit of checking before you commit. No graded evaluation here, but you won't get far without these three commands, so take the time to actually read the output instead of skimming past it.