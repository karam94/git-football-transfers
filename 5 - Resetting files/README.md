# git-football-transfers

## 5 - Resetting files

### NOTE: For this section, perform all commands from within the '5 - Resetting files' folder of this project.

### Resetting

Resetting works by moving the current `HEAD` pointer to another (most oftenly, an older) commit and continuing work from that point forwards. The commit reverted from eventually gets garbage collected and seizes to exist.

However as this is a pragmatic crash course, I think it's better that resetting is learned through understanding by practice & when to use the command, rather than worrying deeply around the underlying theory in this case.

There are three types of resetting in Git:

- `git reset --hard`
  - Sets our Working Area & Staging Index to match the state of the Local Repository.
  - This therefore removes any file changes, commits, stagings or deletions we may have made but have not pushed to the repository yet.
  - This means that any local changes, get reset and lost forever!
- `git reset --mixed` (also the default setting if you do a merely a `git reset`)
  - Leaves changes within the Working Area, but resets the Staging Index to match the state of the repository.
  - This therefore removes any commits, stagings or deletions we may have made, but have not pushed to the repository yet.
  - Notice that unlike the `git reset --hard` option, local changes remain intact and are not lost.
- `git reset --soft HEAD^`
  - Sets our Working Area & Staging Index to match the exact state of a specific commit.
  - This therefore removes any commits previously made after the commit we move to, however file changes & stagings remain intact.
  - You probably won't use this very often. `HEAD^` can be interchanged with `HEAD~` or `HEAD~2`. They represent how many commits behind we wish to move to. Feel free to research this more in your own time.

## --HARD

News has just come in that Liverpool have signed Ronaldinho. Add him to `Liverpool.txt`. Open the text file and add him:

```bash
Salah
Mane
Firmino
Ronaldinho
```

Now create a new file called `ManchesterUnited.txt` in the same directory as we will soon have to add transfers for them too.

If we run `git status` we can see the files are unstaged. Let's stage these changes by doing `git add .`. Now look at `git status`. What do you see?

Oops, it turns out that Ronaldinho actually retired years ago and that the news was false. Let's reset the changes we made by running `git reset --hard`.

You should notice that both the changes to `Liverpool.txt` and the new file `ManchesterUnited.txt` you staged have disappeared completely, matching our working directory to the repository state.

## --MIXED

News has just come in that Liverpool have signed Mbappe. Add him to `Liverpool.txt`. Open the text file and add him:

```bash
Salah
Mane
Firmino
Mbappe
```

If we run `git status` we can see the files are unstaged. Let's stage these changes by doing `git add .`. Now look at the change in `git status`.

Oops, it turns out that Mbappe hasn't signed for Liverpool yet, but may do so within the next couple of hours of the transfer. We therefore don't want to completely remove our change, we just want to unstage it for the time being. Do a `git reset` followed by a `git status`.

You should notice that Mbappe still exists within `Liverpool.txt` however, the change has been unstaged and needs to be added again whenever confirmation of the transfer comes in again.

## --SOFT

Due to the nature of this crash course focusing on parts of Git that you will regularly use, we won't cover an example of a --SOFT reset.

## Commands you have learned this module!

`git reset --hard` - Nukes all changes you have made and resets your working directory to match the repository. This is a DANGEROUS command!

`git reset --mixed` - Nukes all stagings you have made but have not pushed to the repository. Your working directory remains intact and these files need to be staged again.

`git reset --soft` - Allows resetting our working directory to match a previous commit on the repository.
