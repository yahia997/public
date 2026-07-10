# Your first GitHub repository !!
Welcome! This guide walks you through creating your very first project with Git and GitHub, one small step at a time. Don't worry about memorizing everything — just follow along.

## Install Git
1. If you did not install git before on your computer, go to: [git-scm](https://git-scm.com/install/) and install git.

2. Check git is working on your computer by using this command in your terminal:
```bash
git --version
```

3. Tell Git who you are, Use the same email you'll use for GitHub — it helps link things together later.
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
## GitHub
If you have not created an account on GitHub, go to [github](https://github.com/) and create an account.

## Init your repository
There are two ways to initiate your github repository:
1. You have an old project and want to turn into git repo (repo is short for repository).
2. Clone an existing repo and work inside it.

We will go with the second option here, using our own repository.

### Clone the project repository
Clone our repo to get a local copy on your machine:
```bash
git clone https://github.com/yahia997/public
```

Then move into the cloned directory, using the change directory command.
```bash
cd public
```

> Notice this directory is already a git repository — you don't need to run `git init` here, since cloning sets that up for you automatically.

## Git Status

Type the following command inside your repository's directory:
```bash
git status
```

You'll see something like this:
```text
On branch master
Your branch is up-to-date with 'origin/master'.
nothing to commit, working tree clean
```
This means every file Git knows about is unmodified — nothing's changed since the last commit.

### Add content to your project
To be able to see what is going on we will add a text file with some content.
```bash
touch a.txt # create a new file
echo "Hello, world!" > a.txt # overwrite content of "a.txt" to be "Hello, world!"
cd .. # move back to the project's root
```

Ensure that `a.txt` is inside the root directory of the repo.

> Now type `git status` again. Notice `a.txt` shows up as **untracked** — Git sees the file, but isn't tracking changes to it yet.

### Track your files
This phase is called **Staging**. Use the following command to tell git which files to track.
```bash
git add .
```
> Use `.` to track all files.
```bash
git add <file-name> # To track a single file
```

> Type `git status` again. Notice `a.txt` has moved from "Untracked files" to "Changes to be committed" — it's now **staged**.

### Commit your changes
```bash
git commit -m "Initial commit"
```
This is called a commit — a saved snapshot of your project at this moment, with a short message describing it. `"Initial commit"` is a very common message for the very first one.

> Type `git status` one more time. What's different now compared to right after staging? Your working tree should be clean again — the staged changes have been saved into a commit, so there's nothing left to commit.

### Create your own remote repository on GitHub
Since you cloned our repo, it's still pointing to our GitHub — but you can't push your changes there. You'll need your own public repository to submit your work.

Go to your GitHub account and find the `New repository` button, press it, and follow the instructions to create your own **public** repo.

> Leave it completely empty — no README, no `.gitignore`, no license file. If GitHub adds any files automatically, your push later on may run into a conflict since your local repo already has its own commit history.

### Connect your local repo with your remote repo
GitHub will show you a URL like `https://github.com/yourusername/your-repo.git`. Since the cloned project already has an `origin` remote (pointing to our repo), you'll need to update it to point to yours instead:
```bash
# use your own github repo url
git remote set-url origin https://github.com/yourusername/your-repo.git

# we will explain the concept of branching later
git branch -M master # makes sure you are on the "master" branch
git push -u origin master # uploads your commit to your own GitHub repo
```

Refresh your GitHub page — your files should now appear online. 🎉

## How to submit your solution to evaluate ?
1. Ensure you create an account on our website.
2. Install cli tool from this repository `ieee_cli.exe`.
3. Run the cli tool using:
```bash
./ieee_cli.exe
```
Then login with your account.

4. Push your solution to your public github repo (the one you created above).
5. Choose a project and then project's phase to submit.