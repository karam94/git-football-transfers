# git-football-transfers

## 6 - Using the stash

### NOTE: For this section, perform all commands from within the "6 - Using the stash" folder.

### Stashing

The stash is a storage area within a Git repository. It exists for convenience to allow us to temporarily stash/save work and pick it up again later.

Create a file called `Arsenal.txt` and run `git stash --include-untracked`. Can you guess what the `--include-untracked` flag does?

Now run `git stash list`. Here you will see the stash that has been created along with a number that represents it, we'll refer to this as `STASH_NUMBER`. Copy that hash.

Your changes with the new `Arsenal.txt` file have been stashed.

You cannot find the file anymore because the repository has been reset for you to do something else and come back to the changes later.

You can restore the state of your repository from the stash using the `git stash apply STASH_NUMBER` command.

Your `Arsenal.txt` file should now be restored!

You can delete the stash using `git stash drop STASH_NUMBER`.

Remember to delete `Arsenal.txt` prior to starting the next module.

## Commands you have learned this module!

`git stash --include-untracked` - Takes a current snapshot of the working directory and stores them in the stash, followed by reverting the changes in the working directory.

`git stash list` - Lists all current stored stashes.

`git stash apply STASH_NUMBER` - Applies the changes stored within a stash, to the working directory.

`git stash drop STASH_NUMBER` - Deletes a specific stash from the overall stash.
