##Git Commands and GitHub Functions

This document contains Git commands and GitHub functions I learned from Udacity's [How to Use Git and GitHub Course](https://www.udacity.com/course/how-to-use-git-and-github--ud775) as well as more things from self-work/study.

####Key Things and Concepts

**version control** - a way to keep different versions of files saved at different points in time. Dropbox, Wikipedia, and Google Docs all have they own way of doing version control.

**Git** - a version control system. Saving versions is done manually and locally on your computer.

**shell** - a command line interpreter that executes commands. The windows command prompt is a commonly known shell.

**Git Bash** - a shell where `git` is a known command. Git Bash is a common way to use Git.

**GitHub** - a website that hosts online repositories via interaction with Git. Offers features for collaboration.

**repository** -  a directory which utilizes git version-control, often called a _repo_. It contains commits (unless you've just initializied/created a repository). 

**working directory** - the area on your computer where you make changes before committing changes.

**staging area** - the middle ground between the working directory and committing a change. Use this area to review changes and ensure your commits are logical.

**commit** - a saved version of a file. Multiple files can be changed in one commit.

**branch** - a history of commits.

**remote** - the online repository a local repository updates and/or gets changes from.

**HEAD** - the most recent commit on a branch. This updates automatically when a new commit is made.

**master** - the default branch in Git.

**origin** - the default remote.

**upstream** - a common-practice remote name for the original repository when you're working with a fork but need to update your local remote (origin/master) with the original repository.

####Common Workflow Situations

**Making a repository** - Create a directory, either with Windows Explorer (if you're on PC) or in Git Bash with `mkdir`. Run `git init` and the repository is created.


**Working on a project, updating it, putting it on GitHub** - make changes in the working directory. Add the changes with `git add`. Note you can add more than one file. Commit your change with `git commit`. Write a commit message either with the `-m` argument in `git commit` or in your editor of choice. Create the repository on GitHub. Add the remote with `git remote add origin URL`. Put your local changes onto the remote with `git push origin master`.

**Merging two branches, deleting a branch** - checkout the branch you want to update. Run `git merge other-branch-name`. Run `git add changed-file`. Commit it. Delete the old branch with `git branch -d branch-name`.

**Resolving a merge conflict** - open your editor of choice. You can search for the conflict by searching for the repeated less than sign, like this : `>>>>>`. The part after the `>>>>>` is your code. The code `|||||` is the original code. The code after the `<<<<<` is the conflict code that someone else wrote. Make the appropriate changes, delete the marker lines, then add and commit the merge change.

_Note: If you experience a merge conflict in a pull request due to changes in code in the original repository (not your fork), you'll need to update your local remote (typically origin/master) by creating a new remote (called upstream) that points to the original repository. You'll then fix any conflicts, push the changes to your fork, and your pull request should automatically update to be mergeable._

**Contributing code to a project** - make new code on separate branch. This is considered a common practice. Push it to your fork. Open a pull request on GitHub.

####Git Commands

**`git init`** - use to create a repository on your computer. Do this in a directory.

**`git add`** - use to add a file to the staging area (also called the index). The file to add is the argument. 

_Ex: `git add info.txt`_

Note the staging area is the place between the working directory and the master branch.

**`git commit`** - use to add a file to a branch from the staging area. With no arguments, you can configure Git to open up your editor of choice and write the commit message there. You can also write `git commit -m` then the the commit message in parentheses.

_Ex: `git commit -m "Fix typo"`_

**`git diff`** - with no arguments, see changes you've made between the working directory and the staging area. Run with the argument `--staged` to see differences between changes in the staged area and the branch. You can have two arguments after diff to compare to different things, such as commits or branches. 

_Ex: `git commit master origin/master`_

**`git log`** - see history of commits of current branch with no arguments. Add argument of another branch to see commits of that branch. 

_Ex: `git log origin/master`_

**`git status`** - see changes made in working directory or in staging area. Takes no arguments.

**`git checkout`** - switch to a branch to work on it. Needs the branch as an argument.

_Ex: `git checkout Korean`_

**`git clone`** - downloads a repository from GitHub onto your computer and automatically creates a remote. Add the url for the argument. 

_Ex: `git clone https://github.com/ellereeeee/reflections.git`_

**`git branch`** - shows branches in repository when run with no arguments. Run with argument to create new branch. 

_Ex: `git branch new-feature`_

**`git remote`** - show what remotes you have.  
**`git remote -v`** - show the url fetch and push remotes. The `-v` arguments stands for "verbose."  
**`git remote add`** - create a remote that lets you push and pull changes to GitHub (the cloud, so to speak). Takes two arguments, the name of the new remote and a URL. 

_Ex: `git remote add origin https://github.com/ellereeeee/reflections.git`_


**`git push`** - update local commits to a remote repository on GitHub. Takes two arguments, the remote and the local branch respectively. Ex: `git push origin master`. This pushes the local master branch onto the origin remote repository on GitHub.

**`git fetch`** - updates your local remote branch (but not your working directory!) from the remote repository. The local remote branch's name is the remote name and branch name designed by a backslash (often called origin/master). Needs no arguments.

**`git merge`** - merges a branch into your current checked out branch. Only needs on argument, but some people may put two to visualize what is being merged. 

_Ex: The following commands are different but the outcome is the same._

1) The master branch is checked out. You run `git merge coins`. The coins branch is merged into the master branch, assuming there are no conflicts.

2) The master branch is checked out. You run `git merge master coins`. The coins branch is merged into the master branch, assuming there are no conflicts.

**`git pull`** - updates your local branch (including your working directory) from the remote repository. This is the same thing as running `git fetch` then `git merge`.

####GitHub Functions

**fork** - both a noun and a verb. Makes a copy of someone else repository onto your GitHub account. Allows you to modify your copy of someone else's project without modifying the original creator's repository. Credits the original author. Similar to cloning, except all copying is done on GitHub.

**pull request** - notifies someone else of a change or update you made for review, and to possibly merge it into a branch. _Merge request_ may be a more approriate term since you a requesting someone to merge your code into another branch of code. It it named _pull request_ because they may be pulling your code into the other piece of code. Not to be confused with the `git pull` command!