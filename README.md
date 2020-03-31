# git-football-transfers

This repository contains a number of activities to help learn a handful of Git concepts, by taking control of an imaginary football transfer window!

Part of a **pragmatic** crash course I am building to help software developers learn Git. The reason why I focus on pragmatism is because I believe it's less important for developers to become so-called Git experts as most courses aim to cover and instead focus on a leaner approach to get developers comfortable with Git, focusing on the areas which will be more prominent throughout their day to day roles.

The tasks will revolve around playing God, in today's hectic football transfer market.

## Proposed Topics

- Visualising a repository.
- Branches, pulling & checking out code.
- Pushing code.
- Removing files & reverting commits.
- Resetting files.
- Using the stash.
- Merging and merge conflicts.
- Rebasing and merge conflicts.
- Rewriting history with the interactive rebase.
- Gitflow.
- Trunk Based Development.
- Recommended Git/Source Control GUIs.

## Pre-requisites (READ ME)

If you do not have Git installed, follow this guide: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git

These terms will be referred to within the crash course, so it's important you have a rough idea what they mean.
If you still feel confused, they'll make more sense as you go through the different modules.

- Git is made up of three different levels:
  - Your Working Directory
    - These are your local files, on your local machine which you can make modifications to. Basically, it is where you are currently working.
    - Modified or new files at this point are considered untracked by the Git repository. This means that despite your changes, they are not saved yet to the Git repository.
  - The Staging Index
    - This is the staging area between your Working Directory & Local Repository.
    - This is where untracked files become tracked files once you do a `git add`.
    - Once files become tracked, the Git repository starts to care about them and they are ready to be pushed to the Git repository.
  - The Local Repository
    - This is the `.git` folder within your Working Directory and contains a record of the current repository files and project history such as commits, trees, blobs, etc. It is a hidden folder, so to see it, enable hidden folders on your machine.
    - If your repository has a `remote` set, this will be a reference to a remote repository such as a GitHub repository or Bitbucket repository, for example.
    - Files move from the Staging Index to the Local Repository after doing a `git commit`.
    - They then move to the Remote Repository after doing a `git push` if a `remote` is set.

## Commands covered throughout the crash course

`git clone REPO_URL` - Clones a repository.

`git remote -v` - View a repositories current remotes.

`git remote rm REMOTE_NAME` - Remove a repositories remote.

`git remote add REMOTE_NAME REPO_URL` - Add a new remote to a repository.

`git log` - View a detailed log of the history of commits within a repository.

`git log --graph --decorate --oneline` - View a fancy, graphical log of the history of commits within a repository.

`git show HASH` - View detailed information on the history of a particular commit.

`git blame FILENAME` - View the history of a specific file within the repository.

`git pull` - Pulls down the latest changes of a branch, from the remote repository.

`git checkout BRANCHNAME` - Pulls down and switches to a specific branch locally, from the remote repository.

`git branch` - Displays the repository branches available locally.

`git switch BRANCHNAME` - Switches to the local branch specified.

`git status` - Displays a summary of any changes in the local repository that have not been committed to the index yet.

`git diff` - Displays the changes made in files within the current working directory that have not been committed to the index yet.

`git add` - Adds a file or numerous files to the local index, ready to be committed and pushed to a remote repository.

`git commit -m COMMIT_MESSAGE` - Commits changes made to the local index, to the local repository with a user specified commit message.

`git push` - Pushes the changes made to the local repository, to the remote repository.

`git reset --hard HEAD` - Resets the contents of the local working area, to match those of the remote repository.

`git rm --cached` - Reverses the action of adding a file from the working area, to the local index. It therefore becomes untracked again (reverses a `git add` for a specific file).

`git revert HASH` - Creates a new commit, which contains the exact reverse of another commit specified as the HASH parameter.

`git reset --hard` - Nukes all changes you have made and resets your working directory to match the repository. This is a DANGEROUS command!

`git reset --mixed` - Nukes all stagings you have made but have not pushed to the repository. Your working directory remains intact and these files need to be staged again.

`git reset --soft` - Allows resetting our working directory to match a previous commit on the repository.

`git stash --include-untracked` - Takes a current snapshot of the working directory and stores them in the stash, followed by reverting the changes in the working directory.

`git stash list` - Lists all current stored stashes.

`git stash apply STASH_NUMBER` - Applies the changes stored within a stash, to the working directory.

`git stash drop STASH_NUMBER` - Deletes a specific stash from the overall stash.

`git checkout -b BRANCH_NAME` - Checks out a branch specified as parameter from the remote repository.

`git merge BRANCH_NAME` - Merges the branch specified as parameter in to the current branch checked out.

`git branch -d BRANCH_NAME` - Deletes the branch specified as parameter from the local repository.

`git rebase BRANCH_NAME` - Takes the content of the branch specified as parameter and modifies the local branch to be the branch specified's commits plus the current local commits on top of that new base.

`git rebase --continue` - Continues the process of attempting a rebase, moving on to the next commit to try and apply.

`git rebase --interactive` - Starts an interactive rebase on the current branch.

`git log --oneline` - Shorter, more concise version of `git log`.
