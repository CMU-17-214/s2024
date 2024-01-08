# Git -- The Basics

For all labs and homeworks, you are required to submit your work by pushing changes to your repositories. Throughout the semester you will learn to work with *git* and to use best practices.

Git is a version control system, which is a fancy way to say that you can take *named* snapshots (i.e. make saves) of your code base with it throughout development, and you can easily revert back to any such saves should something go wrong. Sooner or later you will write code that breaks, and you’d wish to “undo” what you wrote. Without git, you’ll have to figure out what you changed and revert them manually, which is time-costly and error-prone. With git, if you made a save when your code was working, you can revert back to that in one command. You also document your work incrementally for others.

## First Steps: Submitting Work

Let's start with the basics on the command line:

````bash
git add <filename1> <filename2>
git commit -m "<some message>"
git push
````

**git add** adds files to the staging area, **git commit** saves everything on the staging area along with the given commit message, and **git push** records local commits to the remote repository. After pushing changes you should see them on GitHub.



**Beyond the command line.** You can also push changes to your repository using the VSCode UI or use [GitHub Desktop](https://desktop.github.com/). In VSCode, the source control tab (3rd from the top) provides you with an interface where you can stage, commit, and push changes. Clicking the + icon on the file stages it to be committed. Once you have staged all of your files, you can use the text box to add a commit message and press commit. You can then use the UI to push. 



## Important Git Concepts

- **Git Repository:** A git repository is a database of files and their history. On a local computer it will be stored in a .git directory. A repository on your computer is called a *local repository*, and a (typically shared) repository stored somewhere online (e.g. on GitHub) is called a *remote repository*. 
- **Git Commit:** A git commit is a snapshot / save of your git repository. You make a save of your code base by making a git commit. A commit has an ID and a description. It follows another commit. You can later revert back to it. 
- **Working directory:** Code from a git repository can be *checked out* in a directory. This will copy all files from the (typically last) commit from the git database to your directory where you can edit them.
- **Staging Area:** Before you can make a git commit, you need to specify the files you want to include in your commit. In git you do this by *adding* them to the staging area, where you can double check that you are saving what you want. The *commit* command will create a commit of all files staged, but not of other changed files in your working directory.
- **Remote Repository:** A remote repository is like a folder on Google Drive. Just like how you could backup your local files online to Google Drive, you can backup your local Git Repository online as a remote repository. This also enables collaboration: remote repositories are usually shared, when your collaborators *push* (upload) new changes to a shared remote repository, you can *fetch* (download) them to your computer. 
- **Branching:** Git branching allows you to create new development paths for your code. Each path is called a branch. Changes on one branch are independent from changes made on a different branch. Later, if desired, changes from different branches can be merged together. People commonly use branching when implementing new features. They create a new “development branch” and implement new code on it, keeping the default “master branch” clean. If the new code works out, they merge changes from the development branch into the master branch. If it doesn’t work out, they just discard the development branch. This ensures that the master branch always contains working code. 



![img](https://lh4.googleusercontent.com/dGUCNsOeIKcHSjAEj1XARjgulfXrbndajIB8KfpuJjLvOWFIcEH-Ts6R5bsvViIQf0YxUSBxXtURK0iEmaLh8Zy3BXWHLpgbAWFdpVfG_WAQ6INa3mI_pyzpve0GZLN5FpfK7lPJ0X-ps8ckeqF9JQ)

## Useful Git commands

- `git clone <remote repository link>` (Clone, i.e. download in entirety a git repository from a remote location and check it out in a local working directory)
- `git pull` (Pull, i.e. download, any new changes from the remote repository not previously downloaded and merge them into your local working directory)
- `git add <filename1> <filename2>...` (Add files to the staging area)
- `git status` (Shows which files have been changed and which files are on the staging area)
- `git commit -m "<some message>"` (Make a commit saving everything on the staging area. The save is tagged with a message <some message>)
- `git log` (List all the commits you’ve made)
- `git push` (Push, i.e. upload, any new commits you made locally to the remote repository)
- `git branch "<branch name>"` (Create a new branch named <branch name>)
- `git checkout <branch name>` (Check out files from the git repository to your local working directory of the branch named <branch name>)

## Good Git Practices 

Good practices help you and other engineers understand your development process. Especially:

- Make clean, single purpose commits.
- Leave meaningful but concise commit messages. 
- Commit early, commit often
- Don’t alter published history
- Don’t commit generated files 

## Useful resources to learn git

- [Git cheatsheet](https://education.github.com/git-cheat-sheet-education.pdf) -- A concise guide for git commands
- [Pro Git book](https://git-scm.com/book/en/v2) -- expert guide to Git written by GitHub founder
- [Git Game](https://learngitbranching.js.org/?locale=en_US) -- interactive tutorial and playground for practicing branching and merging

