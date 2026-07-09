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
2. Create an empty repo on github then add your content later.

We will go with the first option here.

### Create your project's directory
```bash
mkdir myproject
```

Then move to the created directory, using change directory command.
```bash
cd myproject
```

### Add content to your project
To be able to see what is going on we will add a text file with some content.
```bash
touch a.txt # create a new file
echo "Hello, world!" > a.txt # overwite content on that file "a.txt" to be "Hello, world!"
```


### Your first git command !
To change this project into a git repo, type the following command in your terminal:
```bash
git init
```

This creates a new subdirectory named `.git` that contains all of your necessary repository files a Git repository skeleton. At this point, nothing in your project is tracked yet.

### Track your files
This phase is called **Staging** as we described earlier. Use the following command to tell git which files to track.
```bash
git add .
```
> Use `.` to track all files.
```bash
git add <file-name> # To track a single file
```

### Commit your changes
```bash
git commit -m "Initial commit"
```
This is called a commit — a saved snapshot of your project at this moment, with a short message describing it. `"Initial commit"` is a very common message for the very first one.

### Create your remote repository on github
Go to your github account and find a button of `New repository`, just press it and follow the instructions.

### Connect your local repo with the remote repo
GitHub will show you a URL like `https://github.com/yourusername/your-repo.git`. Run:
```bash
# use your own github repo url
git remote add origin https://github.com/yourusername/your-repo.git

# we will explain the concept of branching later
git branch -M main # makes sure you are on the "main" branch
git push -u origin main # uploads your commit to GitHub
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

4. Push your solution to a public github repo.
5. Choose a project and then project's phase to submit.


