# git-football-transfers

## 7 - Merging and merge conflicts

### NOTE: For this section, perform all commands from within the "7 - Merging and merge conflicts" folder.

![Merge Branch]("MergeBranch.png?raw=true")

### Merging

Merging quite simply, is when changes made to files on one branch now need to be integrated in to another branch.

For example, if a development team uses feature branches, this means that prior to developing a feature, they create a branch off master where they make and commit their changes to. Imagine master as the branch that represents the codebase in production.

Once the work is done and tested, that feature branch then has to be merged back in to the master branch so that it can be deployed to production.

This is merging.

### Merge Conflicts

Due to the nature of software development, it isn't uncommon for changes to be made to the same files on occasion within two branches.

Let's assume we have two reporters on football transfers. Alice & Bob.

Alice receives information that Manchester City have just signed Pogba and therefore adds him to `ManchesterCity.txt` on `line 4`, on her feature branch.

Bob has meanwhile also received information that Manchester City have just signed Lewandowski and therefore adds him to `ManchesterCity.txt` on `line 4`, on his feature branch.

Alice stages, commits and pushes her change to the master branch.

Bob a couple of hours later, decides to do the same. However is unable to do so. Can you guess why?

Firstly, Bob will have to pull down the latest iteration of the master branch, if he is to push his changes to it.

Secondly, Bob has encountered a merge conflict. This is because both himself and Alice, have modified the same line of what would usually be code.

Bob deals with the merge conflict, by moving his change to `line 5`. This then creates a merge commit that he can push.

This merge conflict was an easy fix, however with real source code, if two peoples changes overlap, extra care has to be taken to ensure that the merged output has not negatively impacted the output of the new code structure within the file once executed.

### Simulating a Merge Conflict

Pretend you are Alice. Create your new feature branch `git checkout -b Alice` and your current branch should automatically switch. If not, use `git switch Alice`.

Add Pogba to `ManchesterCity.txt` and stage and commit your changes using `git add .` followed by `git commit -m "Add Pogba to Manchester City"`.

Now pretend you are Bob. Switch back to the master branch using `git switch master`. Create your new feature branch `git checkout -b Bob` and your current branch should automatically switch. If not, use `git switch Bob`.

Add Lewandowski to `ManchesterCity.txt` - notice Pogba is no longer in the file here, as Bob's branch is based on the master branch - and as before, `git add .` followed by `git commit -m "Add Lewandowski to Manchester City"`.

You are now Alice again and now want to integrate your changes in to the master branch by merging your Alice branch in to master.

Switch back to the master branch using `git checkout master` and now run `git merge Alice`. This should merge successfully. You can confirm this by seeing if Pogba is in `ManchesterCity.txt` on your master branch. You can delete Alice's branch which is now obsolete as it has now been merged in using `git branch -d Alice`.

You are now Bob again and now want to integrate your changes in to the master branch by merging your Bob branch in to master.

You are already on the master branch, so simply run `git merge Bob`. Congratulations, you have a merge conflict!

```git
git merge Bob
Auto-merging 7 - Merging and merge conflicts/ManchesterCity.txt
CONFLICT (content): Merge conflict in 7 - Merging and merge conflicts/ManchesterCity.txt
Automatic merge failed; fix conflicts and then commit the result.
```

You need to resolve the conflict from:

```text
Aguero
Laporte
Ederson
<<<<<<< HEAD
Pogba
=======
Lewandowski
>>>>>>> Bob
```

to and save the file:

```text
Aguero
Laporte
Ederson
Pogba
Lewandowski
```

Once you have solved the merge conflict, you can `git add .` to stage the modified file, `git commit -m "Fixed merge conflict"` and delete the Bob branch using `git branch -d Bob`.

```text
git log
commit 755ffb2c14b3becbce71852be64293d5ae818ebf (HEAD -> master)
Merge: fa9e549 3ed5095
Author: Karam Kabbara <contact@karam.io>
Date:   Sun Mar 29 14:18:30 2020 +0100

    Fixed merge conflict

commit 3ed5095b9bb39be2195fdd1ecdd4c18498b1ecd8 (Bob)
Author: Karam Kabbara <contact@karam.io>
Date:   Sun Mar 29 14:14:02 2020 +0100

    Add Lewandowski to Man City

commit fa9e5496e39236be7c36f0361cefe67129c928cd (Alice)
Author: Karam Kabbara <contact@karam.io>
Date:   Sun Mar 29 14:09:10 2020 +0100

    Add Pogba to Manchester City
```

## Commands you have learned this module!

`git checkout -b BRANCH_NAME` - Checks out a branch specified as parameter from the remote repository.

`git merge BRANCH_NAME` - Merges the branch specified as parameter in to the current branch checked out.

`git branch -d BRANCH_NAME` - Deletes the branch specified as parameter from the local repository.
