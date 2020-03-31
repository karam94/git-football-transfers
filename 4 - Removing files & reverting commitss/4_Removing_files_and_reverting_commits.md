# git-football-transfers

## 4 - Removing files and reverting commits

### NOTE: For this section, perform all commands from within the '4 - Removing files and reverting commits' folder of this project.

### Removing files

Create a third football team within this folder, `Chelsea.txt`.

It is now in what is called your Git working area.

```bash
git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        Chelsea.txt
```

Do `git add .` to move it in to what is called your Git index.

It is now ready to be committed to your local Git repository and then pushed to the remote repository.

```bash
git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   Chelsea.txt
```

However, it turns out that we wanted to add Manchester United instead!

Unfortunately we have already run a `git add .` so if we just locally deleted the file, we would end up needing to do another `git add .` because our Git repository thinks it is now missing a file.

```bash
git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        new file:   Chelsea.txt

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        deleted:    Chelsea.txt
```

The correct way for us to stop tracking this, as if we never added it in the first place, is using the `git rm --cached Chelsea.txt` command.

```bash
git status
On branch master

Untracked files:
  (use "git add <file>..." to include in what will be committed)

        Chelsea.txt
```

As you can see, the file is now untracked again. The command we ran, reversed adding the file to the index from the working area which we did earlier using the `git add .` command.

You can now delete the file using the command `rm Chelsea.txt`.

## Reverting commits

Let's now create that ManchesterUnited.txt file.

You can proceed to `git add .` it and `git commit -m "Added Manchester United"` it.

Oh no. It turns out we actually wanted should've added Arsenal.

How can we now revert our commit?

Remember when we visualised our repository earlier in this crash course? Well, if we want to revert a commit, we need the hash of that commit so we know how to refer to it... `git log`.

Now that you have the hash of the commit you want to reverse, simply do `git revert HASH`. This will create a new commit, that will do the exact opposite of what your last commit did.

If you type `git log` again, you will see that your revert is now there as a new commit and the file commit has been reverted (meaning the added file, has been removed).

## Commands you have learned this module!

`git rm --cached` - Reverses the action of adding a file from the working area, to the local index. It therefore becomes untracked again (reverses a `git add` for a specific file).

`git revert HASH` - Creates a new commit, which contains the exact reverse of another commit specified as the HASH parameter.
