# Working with Remotes

To collaborate on any Git project, you need to know how to manage **remote repositories** —
versions of your project hosted elsewhere (on GitHub, a server, or even another folder on your own
machine). Collaborating means pushing and pulling data between your local repo and these remotes.

## Viewing Your Remotes

When you clone a repository, Git automatically creates a remote called `origin` pointing back to
where you cloned from:

```bash
git remote
```
```
origin
```

Add `-v` to see the actual URLs:

```bash
git remote -v
```
```
origin  https://github.com/schacon/ticgit (fetch)
origin  https://github.com/schacon/ticgit (push)
```

A project can have multiple remotes — useful when collaborating with several people or forks:

```
origin    git@github.com:mojombo/grit.git   (fetch)
origin    git@github.com:mojombo/grit.git   (push)
pb        https://github.com/paulboone/ticgit (fetch)
pb        https://github.com/paulboone/ticgit (push)
```

## Adding a Remote

To add a new remote under a shortname you can reference easily:

```bash
git remote add pb https://github.com/paulboone/ticgit
```

Now `pb` can be used instead of typing the full URL every time — e.g. `git fetch pb`.

## Fetching vs. Pulling

These two commands are often confused, but they behave very differently:

| Command | What it does |
|---|---|
| `git fetch <remote>` | Downloads new data from the remote, but does **not** merge it into your work |
| `git pull` | Fetches **and** automatically merges the remote branch into your current branch |

```bash
git fetch origin
```

`fetch` is the "safe" option — it updates your local record of what's on the server, but leaves your
working files untouched until you decide to merge manually.

```bash
git pull
```

`pull` is more convenient but merges immediately, so make sure your local changes are committed
first to avoid conflicts.

> **💡 Note:** Since Git 2.27, `git pull` will warn you if `pull.rebase` isn't set. Pick a default behavior:
> ```bash
> git config --global pull.rebase false   # merge (default behavior)
> git config --global pull.rebase true    # rebase instead of merge
> ```

## Pushing to a Remote

Once you're ready to share your work:

```bash
git push origin main
```

This only works if you have write access to the remote and nobody else has pushed conflicting
changes since you last fetched. If your push is rejected, fetch and merge their changes first before
trying again.

## Inspecting a Remote

For more detail about a specific remote — tracking branches, push/pull behavior, stale references —
use:

```bash
git remote show origin
```

```
* remote origin
  Fetch URL: https://github.com/schacon/ticgit
  Push URL:  https://github.com/schacon/ticgit
  HEAD branch: main
  Remote branches:
    main       tracked
    dev-branch tracked
  Local branch configured for 'git pull':
    main merges with remote main
  Local ref configured for 'git push':
    main pushes to main (up to date)
```

## Renaming or Removing a Remote

```bash
git remote rename pb paul   # rename a remote
git remote remove paul      # remove a remote entirely
```

Renaming updates all remote-tracking references too — `pb/main` becomes `paul/main`. Removing a
remote deletes all associated tracking branches and config for it.

---

**Quick reference:**

| Task | Command |
|---|---|
| List remotes | `git remote -v` |
| Add a remote | `git remote add <name> <url>` |
| Download changes without merging | `git fetch <remote>` |
| Download and merge changes | `git pull` |
| Upload your commits | `git push <remote> <branch>` |
| Inspect a remote in detail | `git remote show <remote>` |
| Rename a remote | `git remote rename <old> <new>` |
| Remove a remote | `git remote remove <name>` |