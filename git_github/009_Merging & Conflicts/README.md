Branches are great for working in isolation — but eventually, work has to come back together. `git merge` Combines commits from one branch into another. Most of the time, this happens automatically. But if two branches changed the **same lines** of the **same file** in different ways, Git can't decide which version is "right" — and hands the decision back to you. That's a merge conflict.

Conflicted files get special markers inserted directly into them:

```
<<<<<<< HEAD
your version
=======
their version
>>>>>>> other-branch
```

You edit the file to keep what should actually stay, delete the markers, then commit the result.

**What to do:**

- Starting from `main`, create a new branch: `git checkout -b conflict-practice`.
- Edit a specific line in an existing file (e.g., the first line of `README.md`) and commit it on this branch.
- Switch back to `main`: `git checkout main`.
- Edit that **same line** in the **same file**, but to something different, and commit it on `main`.
- Try merging: `git merge conflict-practice`. Git should report a conflict.
- Open the conflicted file — you'll see the `<<<<<<<` / `=======` / `>>>>>>>` markers.
- Resolve it: decide what the line should actually say, delete the markers and the version(s) you don't want.
- Stage the resolved file: `git add <file>`, then finish the merge: `git commit`.
- Push: `git push`.
- Submit your repository link through the platform to trigger evaluation.