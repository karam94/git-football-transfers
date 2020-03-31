# git-football-transfers

## 1 - Visualising a repository

The first step towards being able to visualise a repository using Git requires pulling down a remote Git repository first to ones local machine.

### NOTE: For this section, perform all commands from within the ROOT folder of this project once you have completed the Cloning step.

### Cloning

This is called 'cloning' a repository and can be done by performing a `git clone` command like so:

`git clone https://github.com/karam94/git-football-transfers.git`

This downloads a clone of a repository on to your local machine. This is known as your working directory.

This is where you can manipulate files within the codebase, ready to push back up to the repository in the future.

In order to complete this crash course, you need to clone this repository on to your local machine.

### Remote

If you go to the root of the repository you have just cloned locally on your machine and run `git remote -v` you will see an output like below:

```bash
origin  https://github.com/karam94/git-football-transfers.git (fetch)
origin  https://github.com/karam94/git-football-transfers.git (push)
```

Git knows where you cloned the repository from and therefore where you will **_most of the time_** want to push changes back up to.

Unfortunately, as you are not the owner of this repository, you will not have access to be able to push changes back up. This is fine for the purpose of this crash course.

In order to remove the remote references, you can use the `git remote rm` command. DO NOT DO THIS HOWEVER.

It is possible to add new remotes to the repository using the `git remote add origin https://github.com/you/repo.git` command.

However this is not necessary for this crash course as all git work will be done locally.

### Log

It is possible to view the history of commits to a repository by ensuring you have navigated to the root using the `git log` command.

However, this produces quite a terse output which may be overwhelming for some, particularly in large repositories.

Despite this, take note of how each commit has a hash next to it. This is a unique identifier that represents that hash in particular. Copy one of the hashes for later.

For the sake of simplicity, I will refer to the hash as 'd670460b4b4aece5915caf5c68d12f560a9fe3e4', so that it is clear where you should use yours.

Instead it is also possible to use the `git log --graph --decorate --oneline` command to produce a more graphical representation, similar to what is available in GUI-based source control applications such as GitHub Desktop, SourceTree & others.

If you now use the `git show d670460b4b4aece5915caf5c68d12f560a9fe3e4` command, you will have displayed information specific to that commit.

You can also specifically visualise the history of a particular file using the `git blame README.md` command.

## Commands you have learned this module!

`git clone REPO_URL` - Clones a repository.

`git remote -v` - View a repositories current remotes.

`git remote rm REMOTE_NAME` - Remove a repositories remote.

`git remote add REMOTE_NAME REPO_URL` - Add a new remote to a repository.

`git log` - View a detailed log of the history of commits within a repository.

`git log --graph --decorate --oneline` - View a fancy, graphical log of the history of commits within a repository.

`git show HASH` - View detailed information on the history of a particular commit.

`git blame FILENAME` - View the history of a specific file within the repository.
