# git-football-transfers

## 8 - Rebasing and merge conflicts

### NOTE: For this section, perform all commands from within the "8 - Rebasing and merge conflicts" folder.

![Rebase Branch](RebaseBranch.png?raw=true)

### Rebasing

Rebasing aims to solve the same problem that merging does which we covered in the previous module, but in a different way.

Unlike in a traditional merge where two branches are brought together and a merge conflict is manually solved by an individual, to create a merge commit which unites both branches, rebasing instead takes a replay-sequential approach.

The rebase sequentially goes through the new commits on the branch being merged in, commit by commit and tries to automatically replay them on top of the master branch that is being merged in to. Where manual intervention is required due to a conflict for a particular commit, a conflict can be solved.

Once the commits from the branch being merged in, have all been applied on top of the master branch being merged in to, the rebase is completed and thus the merge is complete.

The main difference here between a traditional merge and a rebase is that a rebase is a destructive action, as it involves rewriting history. The commits being rebased on top of the master branch are artificial, unlike a merge which preserves the original commits on the feature branch and instead brings them all in on top of master with a single merge commit.

The advantage of rebasing over merging is that one gets a cleaner and prettier overall git log graph, as it looks like all changes to master, happened sequentially, in perfect timing, as if no merge conflicts ever happened.

Using rebasing over merging is a controversial topic however and is frowned upon in common Git workflows such as Gitflow.

We'll look at one of the most controversial things rebasing does, which is rewriting history, in the next chapter.

### Simulating a Rebase with Merge Conflicts

Pretend you are Alice. Create your new feature branch `git checkout -b Alice` and your current branch should automatically switch. If not, use `git switch Alice`.

Add Hazard to `ManchesterCity.txt`, stage and commit your changes using `git add .` followed by `git commit -m "Add Hazard to Manchester City"`.

Now add Messi to `ManchesterCity.txt` and commit your changes using `git commit -m "Add Messi to Manchester City"`.

Now pretend you are Bob. Switch back to the master branch using `git switch master`.

Create your new feature branch `git checkout -b Bob` and your current branch should automatically switch. If not, use `git switch Bob`.

Add Suarez to `ManchesterCity.txt` - notice Hazard is no longer in the file here, as Bob's branch is based on the master branch - and as before, `git add .` followed by `git commit -m "Add Suarez to Manchester City"`.

Bob will now merge his changes on to the master branch using `git checkout master` followed by `git merge Bob`.

```bash
git merge bob
Updating 755ffb2..52f137a
Fast-forward
 7 - Merging and merge conflicts/ManchesterCity.txt | 1 +
 1 file changed, 1 insertion(+)
```

You are now Alice again by doing `git checkout Alice` and now want to integrate your changes in to the master branch by rebasing master on to your Alice branch. Bob merged on to master in the previous step. Alice is now going to rebase on to master.

```bash
git checkout Alice
git rebase master
First, rewinding head to replay your work on top of it...
Applying: Added Hazard
Using index info to reconstruct a base tree...
M       7 - Merging and merge conflicts/ManchesterCity.txt
Falling back to patching base and 3-way merge...
Auto-merging 7 - Merging and merge conflicts/ManchesterCity.txt
CONFLICT (content): Merge conflict in 7 - Merging and merge conflicts/ManchesterCity.txt
error: Failed to merge in the changes.
hint: Use 'git am --show-current-patch' to see the failed patch
Patch failed at 0001 Added Hazard
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
```

Whilst on the Alice branch, execute `git rebase master`. This will open up your favourite text editor and replay the Hazard commit.

```text
Aguero
Laporte
Ederson
Pogba
Lewandowski
<<<<<<< HEAD
Suarez
=======
Hazard
>>>>>>> Added Hazard
```

Once fixed, do a `git add .` to mark the merge conflict as resolved and then do `git rebase --continue` and continue the rebase by replaying the next commit, which is the Messi commit.

Unfortunately we get a merge conflict again, because we solved the previous one by adding Hazard on to the line after Suarez, which is where we added Messi in this commit we are now replaying as part of the rebase.

```text
Aguero
Laporte
Ederson
Pogba
Lewandowski
<<<<<<< HEAD
Suarez
Hazard
=======
Hazard
Messi
>>>>>>> Added Messi
```

Fix it again, do a `git add .` to mark the merge conflict as resolved and then do `git rebase --continue`.

```bash
git rebase --continue
Applying: Added Messi
```

The rebase is now complete. Alice's branch is now equivalent to the latest version of master (which included Bob's change) plus, a replay of her (Alice's) commits directly on top. This means Alice's branch will now be really easy to merge in to master with no conflicts because the only differences after the rebase are now Alice's commits, directly on top.

`git checkout master` and `git merge Alice` will merge in Alice's branch to master.

### The Golden Rule

Never rebase on to shared branches. Rebase only on to a branch, if you are the only person working on that branch. This is why rebasing is useful locally when wanting to merge all the latest changes on to master prior to submitting a pull request as it allows you to guarantee that a merge conflict will be highly unlikely and test the merge locally.

This is why previously, we rebased master whilst on the Alice branch. The rebase affected our local Alice branch.

The reason why rebasing on to shared branches is frowned upon, is because rebasing involves rewriting history. This means that any colleagues who have branches of work, based on existing commits which we have rewritten due to our git rebase on the shared branch and push them up again, our colleagues branches will get very messy when they try to merge their work back in to ours... and we will be making lots of enemies. This is one of the reasons why rebasing is frowned upon by many.

Another reason alongside the fact that rebase rewrites history is that it becomes more difficult to revert a feature on the master branch, as you cannot simply revert the single merge commit, you have to go through all the rebased commits and revert them.

On the other hand, the only real advantage of rebasing over merging is to end up with a cleaner looking git graph. Otherwise, it is no different to a normal `git merge`.

## Commands you have learned this module!

`git rebase BRANCH_NAME` - Takes the content of the branch specified as parameter and modifies the local branch to be the branch specified's commits plus the current local commits on top of that new base.

`git rebase --continue` - Continues the process of attempting a rebase, moving on to the next commit to try and apply.
