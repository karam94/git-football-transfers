# git-football-transfers

## 3 - Pushing code

### NOTE: For this section, perform all commands from within the ROOT folder of this project.

### Pushing

Open `PremierLeague.txt` and change the current champions to Liverpool.

Now type `git status`. You will see that git is telling you that the file has been modified.

Now create a new file called `SerieA.txt` and type `git status`. You will see that git is telling you that a new file has also been added.

```bash
git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   PremierLeague.txt

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        SerieA.txt
```

Open `SerieA.txt` and add write a line inside.

Now type `git diff`. What do you think this command does?

You can add files to be tracked using the `git add` command.

You can either specifically say `git add SerieA.txt` in this case or `git add .` which will add any untracked files within the root of your current directory.

Try doing this and then run a `git status` again.

```bash
git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   PremierLeague.txt
        new file:   SerieA.txt
```

Usually at this point once we are happy with our changes, we would do a `git commit -m COMMIT_MESSAGE_HERE` which commits the changes locally from the working directory to the local repository, ready to be `git push`-ed to the remote repository.

However note that in this case, unless you forked this repository, your remote origin as we have seen earlier will be pointing to one you do not own and therefore do not have the required permissions to push changes to.

We don't want to continue with these changes so we can discard our changes using the `git reset --hard HEAD^` command. Take note of the `^`.

Type `git status`, notice the change?

Be careful when using git reset. We will look at this command and alternatives in more detail later and this is just a taster.

Notice your `PremierLeague.txt` file has now been reset back to contain Manchester City as the champions.

Also note that whilst `SerieA.txt` has not been removed physically from your drive, it is now untracked and unknown to the local Git repository again.

## Ammending

If you made a mistake to a commit prior to pushing it, you can use the `git commit --amend` command.

## Commands you have learned this module!

`git status` - Displays a summary of any changes in the local repository that have not been committed to the index yet.

`git diff` - Displays the changes made in files within the current working directory that have not been committed to the index yet.

`git add` - Adds a file or numerous files to the local index, ready to be committed and pushed to a remote repository.

`git commit -m COMMIT_MESSAGE` - Commits changes made to the local index, to the local repository with a user specified commit message.

`git push` - Pushes the changes made to the local repository, to the remote repository.

`git reset --hard HEAD` - Resets the contents of the local working area, to match those of the remote repository.
