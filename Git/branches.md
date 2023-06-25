# Git branches

## Use case

You’ve decided that you’re going to work on issue #53 in whatever issue-tracking system your company uses.

## Create a new branch

To create a new branch and switch to it at the same time, you can run the `git checkout` command with the `-b` switch:

```bash
$ git checkout -b iss53
Switched to a new branch "iss53"
```

This is shorthand for:

```bash
$ git branch iss53
$ git checkout iss53
```

## List branches

### Local branches

```bash
git branch
```

### Remote branches

```bash
git branch -r
```

### Both local and remote branches

```bash
git branch -a
```

### Add details

```bash
git branch -v
```

### Add more details

```bash
git branch -vv
```

### List all branches with full details

```bash
git branch -vva
```

## Switch branch

For now, let’s assume you’ve committed all your changes, so you can switch back to your `master` branch:

```bash
$ git checkout master
Switched to branch 'master'
```

Next, you have a hotfix to make.
Let’s create a `hotfix` branch on which to work until it’s completed:

```bash
$ git checkout -b hotfix
Switched to a new branch 'hotfix'
```

After committing the work, switch back to the master branch and merge.

## Merge branch

You can run your tests, make sure the hotfix is what you want, and finally merge the `hotfix` branch back into your `master` branch to deploy to production.
You do this with the `git merge` command:

```bash
$ git checkout master
$ git merge hotfix
Updating f42c576..3a0874c
Fast-forward
 index.html | 2 ++
 1 file changed, 2 insertions(+)
```

## Delete branch

After your super-important fix is deployed, you’re ready to switch back to the work you were doing before you were interrupted.
However, first you’ll delete the `hotfix` branch, because you no longer need it — the `master` branch points at the same place.
You can delete it with the `-d` option to `git branch`:

```bash
$ git branch -d hotfix
Deleted branch hotfix (3a0874c).
```

Now you can switch back to your work-in-progress branch on issue #53 and continue working on it.

```bash
$ git checkout iss53
Switched to branch "iss53"
$ vim index.html
$ git commit -a -m 'Finish the new footer [issue 53]'
[iss53 ad82d7a] Finish the new footer [issue 53]
1 file changed, 1 insertion(+)
```

Suppose you’ve decided that your issue #53 work is complete and ready to be merged into your `master` branch.
In order to do that, you’ll merge your `iss53` branch into `master`, much like you merged your `hotfix` branch earlier.
All you have to do is check out the branch you wish to merge into and then run the `git merge` command:

```bash
$ git checkout master
Switched to branch 'master'
$ git merge iss53
Merge made by the 'recursive' strategy.
index.html |    1 +
1 file changed, 1 insertion(+)
```

Now that your work is merged in, you have no further need for the `iss53` branch.
You can close the issue in your issue-tracking system, and delete the branch:

```bash
$ git branch -d iss53
```

## Push the branch to remote

```bash 
git push -u origin <branch>
```

Where `u` stands for `--set-upstream`.

<a id="checkout-a-remote-branch"></a>

## Checkout a remote branch

```bash 
git checkout -t origin/branchname
```

Where `-t` stands for `track`.

---

[Resources](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging "Read more on the Git website")

---

#CommandLine #Git