# Remove a directory from the git history

## Make a fresh clone of `YOUR_REPO`

```bash
git clone YOUR_REPO
cd YOUR_REPO
```

## Create tracking branches of all branches

```bash
for remote in `git branch -r | grep -v /HEAD`; do git checkout --track $remote ; done
```

## Remove `DIRECTORY_NAME` from all commits, then remove the refs to the old commits

Repeat these two commands for as many directories that you want to remove:

```bash
git filter-branch --index-filter 'git rm -rf --cached --ignore-unmatch DIRECTORY_NAME/' --prune-empty --tag-name-filter cat -- --all

git for-each-ref --format="%(refname)" refs/original/ | xargs -n 1 git update-ref -d
```

## Ensure all old refs are fully removed

```bash
rm -Rf .git/logs .git/refs/original
```

### Perform a garbage collection to remove commits with no refs

```bash
git gc --prune=all --aggressive
```

### Check the size of the repository before and after the `gc` with:

```bash
git count-objects -vH
```

## Force push all branches to overwrite their history (use with caution)

```bash
git push origin --all --force
git push origin --tags --force
```

---

#CommandLine #Git