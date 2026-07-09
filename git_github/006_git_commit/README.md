# Git Commit
A **commit** is like a save point in your project.

It records a snapshot of your files at a certain time, with a message describing what changed.

You can always go back to a previous commit if you need to.

### Commit with a messege
To save your staged changes, use `git commit -m "your message"`: 

> Always write a clear message so you and others can understand what changed, This is really important, assume after 2 weeks you returned back to this commit that has unclear messege, you will never understand anything and struggle to figure out.

### Commit All Changes Without Staging
You can skip the staging step for **already tracked files (This means if you added a new file, you should track it first using git add)** with `git commit -a -m "message"`.

This commits all modified and deleted files, but not new/untracked files.

### Write Multi-line Commit Messages
If you just type `git commit` (no -m), your default editor will open so you can write a detailed, multi-line message.

### Commit Message Best Practices:
- Keep the first line short (50 characters or less).
- Use the imperative mood (e.g., "Add feature" not "Added feature").
- Leave a blank line after the summary, then add more details if needed.
- Describe why the change was made, not just what changed.