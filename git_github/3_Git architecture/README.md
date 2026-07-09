# Git Architecture

Every file in a Git project exists in one of **three main states**:

1. **Modified**
2. **Staged**
3. **Committed**

<img src="areas.png">

- **Modified** — You've made changes to the file, but Git hasn't recorded them anywhere yet. The
  change only exists in your working directory.

- **Staged** — You've marked a modified file to be included in your *next* commit. Think of staging
  as a preparation area — a way to choose exactly what goes into a commit before you actually make it.

- **Committed** — The change is now permanently and safely stored in your local Git database
  (called the **repository**, or *repo*). It's officially part of your project's history.

These three states map to three corresponding areas in Git:

| State | Area | What it means |
|---|---|---|
| Modified | Working Directory | Your actual files on disk, as you're editing them |
| Staged | Staging Area (Index) | A snapshot of what will go into the next commit |
| Committed | Git Directory (Repository) | Permanent history — safely saved |

## The Basic Git Workflow

The typical day-to-day flow looks like this:

1. **Modify** files in your working directory.
2. **Stage** the changes you want to include in your next commit (using `git add`).
3. **Commit** — Git takes exactly what's in the staging area and permanently saves that snapshot to
   your project's history (using `git commit`).

<img src="git-basic-commands-768x569.png">

> **💡 Note:** All three steps above — modify, stage, commit — happen entirely on **your local
> machine**. Nothing leaves your computer yet.

## Where Does GitHub Fit In?

Once you've committed your changes locally, you can **push** them to a remote repository — like one
hosted on GitHub — to back them up and share them with others.

A simple way to think about it: staging and committing is like saving a document on your computer,
while pushing is like uploading that saved document to Google Drive so others can access it too.