# Git clone

If you want to get a copy of an existing Git repository — for example, a project you’d like to contribute to — the command you need is `git clone`.

You clone a repository with `git clone <url>`. For example, if you want to clone the Git linkable library called libgit2, you can do so like this:
```bash
git clone https://github.com/libgit2/libgit2
```

That creates a directory named libgit2, initializes a .git directory inside it, pulls down all the data
for that repository.

Then you can enter the created `libgit2` directory to see the project's files.
```bash
cd libgit2
```

If you want to clone the repository into a directory named something other than libgit2, you can
specify the new directory name as an additional argument:
```bash
git clone https://github.com/libgit2/libgit2 mylibgit
```

# Task

To pass this phase you should: 
1. create a new repository into your github account.
2. clone the repo: `https://github.com/libgit2/libgit2`.
3. Then push changes to you github.

<details>
<summary>Hints</summary>

- Use `git add .` and `git commit -m "messege"` to track the clones repo.
- Use `git push` to push to your remote repository.

</details>