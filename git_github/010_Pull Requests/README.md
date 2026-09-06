Merging locally works, but on real teams nobody merges their own branch straight into `main` without anyone else looking at it first. A **pull request (PR)** is GitHub's way of proposing that merge publicly — it shows the diff, lets teammates leave comments, and only merges once someone approves it (or you do, if you're working solo).

A PR isn't a Git command — it's a GitHub feature that sits on top of the branches you already know how to make.

**What to do:**

- Make sure your feature branch from Phase 8 (or a new one) is pushed to GitHub.
- Go to your repository on GitHub — you should see a banner suggesting "Compare & pull request." Click it (or open the Pull Requests tab and create one manually).
- Set the base branch to `main` and the compare branch to your feature branch.
- Write a real title and a short description — what does this branch add or change?
- Open the pull request.
- Review the "Files changed" tab — this is what a teammate would actually see.
- Merge the pull request (the green "Merge pull request" button).
- Confirm on your repo's main page that the change is now part of `main`.
- Submit your repository link through the platform to trigger evaluation.