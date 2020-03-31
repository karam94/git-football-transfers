# git-football-transfers

## 9 - Refactoring history with the interactive rebase

### NOTE: For this section, perform all commands from within the "9 - Rewriting history with the interactive rebase" folder.

### Refactoring history?

Sometimes during development, you make mistakes as you commit frequently.

These might entail typos within the commit messages, commits in the wrong order or just commits that should really be grouped with others.

The interactive rebase on a local branch is a user friendly way that allows you to refactor your commit history, before merging your changes to the master branch.

## The interactive rebase

To start an interactive rebase use the `git rebase --interactive` command. You can also use the shorter `-i` flag instead.

This will open a text file containing a list of your last couple of commits on the branch you are currently on.

```text
pick 52f137a Added Suarez
pick de5b462 Added Hazard
pick d76ed20 Added Messi

# Rebase b61839d..d76ed20 onto 52f137a (10 commands)
#
# Commands:
# p, pick <commit> = use commit
# r, reword <commit> = use commit, but edit the commit message
# e, edit <commit> = use commit, but stop for amending
# s, squash <commit> = use commit, but meld into previous commit
# f, fixup <commit> = like "squash", but discard this commit's log message
# x, exec <command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop <commit> = remove commit
# l, label <label> = label current HEAD with a name
# t, reset <label> = reset HEAD to a label
# m, merge [-C <commit> | -c <commit>] <label> [# <oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified). Use -c <commit> to reword the commit message.
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

Firstly, the style of commit messages is inconsistent. Some commits say "Add" and some say "Added". The tense varies.

In order to rename the final three commits to say "Add Messi" and so forth, I can change "pick" to say "reword" or "r":

```text
r 52f137a Added Suarez
r de5b462 Added Hazard
r d76ed20 Added Messi
```

And as the rebase goes through each commit, modify the commit messages like so:

```text
Add Suarez

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
```

Running `git rebase -i` shows us our commits were successfully renamed:

```text
pick 2ac12d6 Add Suarez
pick b10e057 Add Hazard
pick d941f62 Add Messi
```

How about if we now want to "squash" these three commits, in to a single commit? After all the changes don't overlap and it'll make our commit history look cleaner, right?

```text
pick 2ac12d6 Add Suarez
s b10e057 Add Hazard
s d941f62 Add Messi
```

Since we are squashing the last two commits in to the first one, we change the name of the first commit to include Suarez, Hazard & Messi.

```text
# This is a combination of 3 commits.
# This is the 1st commit message:

Add Suarez, Hazard & Messi

# This is the commit message #2:

Add Hazard

# This is the commit message #3:

Add Messi

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Sun Mar 29 20:35:42 2020 +0100
#
# interactive rebase in progress; onto b61839d
# Last commands done (3 commands done):
#    squash 978cacf Add Hazard
#    squash 10855d7 Add Messi
# No commands remaining.
# You are currently rebasing branch 'master' on 'b61839d'.
#
# Changes to be committed:
#	modified:   7 - Merging and merge conflicts/ManchesterCity.txt
#
```

We can now do `git log --oneline` and we see our commits have been squashed:

```text
3d565a0 (HEAD -> master) Add Suarez, Hazard & Messi
```

This means our branch is now ready to be merged in to master with a cleaner history... however if we do a `git log` we also see that the new squashed commit has the date set of when the squash occurred, not the original commits. This means we have rewritten history... which many may argue defeats the point of using Git in the first place!? I'll let you be the judge of that one.

There are other features of the interactive rebase and merge conflicts can occur (but you deal with them the same way as before and by using `git rebase --continue` as you've already seen in an earlier module). Try them out!

## Commands you have learned this module!

`git rebase --interactive` - Starts an interactive rebase on the current branch.

`git log --oneline` - Shorter, more concise version of `git log`.
