# Tagging

Like most version control systems, Git can mark specific points in a repository's history as
important. This is typically used to mark **release points** — `v1.0`, `v2.0`, and so on. In this phase,
you'll learn how to list, create, share, and delete tags.

## Listing Tags

To see the tags in a repository:

```bash
git tag
```
```
v1.0
v2.0
```

Tags are listed alphabetically — the order has no special meaning.

You can also filter tags by pattern (useful once a project has many):

```bash
git tag -l "v1.8.5*"
```
```
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5.1
```

> **💡 Note:** `git tag` alone implicitly lists all tags. But if you're matching a pattern with a wildcard,
> you must include `-l` or `--list` explicitly.

## Creating Tags

Git supports two types of tags:

| Type | Description |
|---|---|
| **Lightweight** | Just a pointer to a commit — like a branch that never moves. No extra metadata. |
| **Annotated** | A full Git object — stores tagger name, email, date, and a message. Can be GPG-signed. |

**Annotated tags are generally recommended**, since they preserve who created the tag, when, and
why — valuable information for a release history.

### Annotated Tags

```bash
git tag -a v1.4 -m "my version 1.4"
```

View the tag's details, including the tagging message, with `git show`:

```bash
git show v1.4
```
```
tag v1.4
Tagger: Ben Straub <ben@straub.cc>
Date:   Sat May 3 20:19:12 2014 -0700

my version 1.4

commit ca82a6dff817ec66f44342007202690a9376394
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
```

### Lightweight Tags

Just provide a name — no `-a`, `-s`, or `-m` flags:

```bash
git tag v1.4-lw
```

Running `git show` on a lightweight tag skips the extra metadata and shows only the commit:

```bash
git show v1.4-lw
```
```
commit ca82a6dff817ec66f44342007202690a9376394
Author: Scott Chacon <schacon@gee-mail.com>
Date:   Mon Mar 17 21:52:11 2008 -0700

    Change version number
```

## Tagging an Earlier Commit

You don't have to tag `HEAD` — you can tag any commit by passing its checksum (or the first few
characters of it):

```bash
git log --oneline
```
```
15027957 Merge branch 'experiment'
a6b4c974 Create write support
9fceb02d Update rakefile
964f16d3 Commit the todo
```

```bash
git tag -a v1.2 9fceb02
```

This is handy for retroactively marking a release you forgot to tag at the time.

## Sharing Tags

**Tags are not pushed automatically** with a normal `git push` — this is one of the most common
surprises for new Git users. You have to push them explicitly:

```bash
git push origin v1.5
```

To push all tags at once:

```bash
git push origin --tags
```

> **💡 Note:** `--tags` pushes both lightweight and annotated tags. If you only want to push annotated
> tags, use `git push origin --follow-tags` instead.

## Deleting Tags

**Locally:**

```bash
git tag -d v1.4-lw
```

**On the remote** (the tag stays local until you also delete it from the server):

```bash
git push origin --delete v1.4-lw
```

## Checking Out a Tag

To inspect the exact state of the project at a given tag:

```bash
git checkout v2.0.0
```

This puts you in a **detached HEAD** state — you're no longer on any branch, just looking at that
exact commit. You can explore freely, but any commits you make here won't belong to a branch and
can be lost once you check out something else.

If you need to make changes from this point (e.g. patching an old release), create a branch first:

```bash
git checkout -b version2 v2.0.0
```

This gives you a proper branch (`version2`) starting from the tagged commit, so your work is safe
and trackable.

---

**Quick reference:**

| Task | Command |
|---|---|
| List all tags | `git tag` |
| Search tags by pattern | `git tag -l "v1.8.5*"` |
| Create an annotated tag | `git tag -a v1.4 -m "message"` |
| Create a lightweight tag | `git tag v1.4-lw` |
| Tag an older commit | `git tag -a v1.2 <commit-hash>` |
| View tag details | `git show <tagname>` |
| Push a single tag | `git push origin <tagname>` |
| Push all tags | `git push origin --tags` |
| Delete a local tag | `git tag -d <tagname>` |
| Delete a remote tag | `git push origin --delete <tagname>` |
| Check out a tag safely | `git checkout -b <branch> <tagname>` |