# git-football-transfers

## 2 - Pulling and checking out code

### NOTE: For this section, perform all commands from within the ROOT folder of this project.

### Pulling

Code repositories are updated frequently as numerous members of a software development team contribute towards it.

This means that it is inevitable that you will eventually have to pull in the changes to the files made by your peers on to your local machine to ensure your working directory is kept up to date.

This can be done using the `git pull` command and it pulls down changes for the branch you are currently working on.

You may have files pulled down, however will most likely see a message that says `Already up to date.` because you probably pulled this repository down a couple of minutes ago and nobody has made any changes between then and now!

### Checkout

A topic that we will go in to later in this crash course is branching as well as a branching strategy called Gitflow.

A branch is an independent copy of the repository, where a colleague of yours will have made/is pushing changes to and thus it will differ slightly to the main master branch.

Notice the file called `PremierLeague.txt` in the root of this project.

The `git checkout laliga` command pulls in the changes to the files made by your peers on to your local machine, based on that specific branch.

You've just checked out the La Liga branch for this repository. This makes your working directory match that specific branch and tells Git to assume that you are now working on that branch. Any changes you push, any visualisations you perform & so forth, are on the assumption that you are now on the La Liga branch.

Notice the `PremierLeague.txt` file has now been replaced with a `LaLiga.txt` file and that lots of files have now gone missing. This is representative of the contents of the laliga branch.

If you now do a `git pull` (which won't make a difference as nothing has changed on the branch for now), it will pull down changes made to the specific branch you are now working on due to the checkout you performed.

### Branches

All code repositories will have at least one branch, often referred to as the master branch.

Branches are independant sub-copies of a repository which developers might make changes to and work on independently.

Eventually, these branches will need to be merged back in to the master branch.

There are two branches on this repository.

You can view them by typing `git branch`.

You can switch back to the master branch by typing `git switch master`.

We don't need to go in to more detail about branches for now. They will become self explanatory.

## Commands you have learned this module!

`git pull` - Pulls down the latest changes of a branch, from the remote repository.

`git checkout BRANCHNAME` - Pulls down and switches to a specific branch locally, from the remote repository.

`git branch` - Displays the repository branches available locally.

`git switch BRANCHNAME` - Switches to the local branch specified.
