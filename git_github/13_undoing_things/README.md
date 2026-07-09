# Undoing Things

At any point, you may want to undo something. Git gives you several tools for this — just be careful,
since a few of these can lose uncommitted work if used incorrectly.

## Amending a Commit

If you commit too early — forgetting a file, or making a typo in your commit message — you can fix
it with `--amend` instead of creating a messy "oops" follow-up commit:

```bash
git add forgotten_file
git commit --amend
```

This replaces your last commit entirely with a new one, using whatever is currently staged. Your
commit-message editor opens pre-filled with the old message, which you can edit or leave as-is.

> **⚠️ Only amend commits that haven't been pushed yet.** Amending rewrites history — if you
> amend a commit others have already pulled, it'll cause conflicts for them.

## Unstaging a Staged File

Accidentally staged a file you didn't mean to commit yet? `git status` tells you exactly how to undo it:

```bash
git add *
git status
```

Follow the hint:

```bash
git restore --staged CONTRIBUTING.md
```

The file is now unstaged again — but your edits are still there in your working directory, untouched.

> You may see older tutorials use `git reset HEAD <file>` instead — that's the pre-2.23 way of doing
> the same thing. `git restore` is the modern, clearer equivalent.

## Discarding Changes in a File

What if you want to throw away your edits entirely and go back to the last committed version?
`git status` tells you this too:

```bash
git restore CONTRIBUTING.md
```

> **⚠️ This is a destructive command.** Any uncommitted local changes to that file are gone for good.
> Only use it when you're certain you don't need those changes.

---

**Quick reference:**

| Situation | Command |
|---|---|
| Fix your last commit (message or forgotten file) | `git commit --amend` |
| Unstage a file (keep the edits) | `git restore --staged <file>` |
| Discard uncommitted edits in a file | `git restore <file>` |

> **💡 Good news:** Anything that's been *committed* in Git can almost always be recovered later, even
> from deleted branches or overwritten commits. It's only uncommitted work that can truly be lost —
> which is exactly why commits are cheap and worth making often.