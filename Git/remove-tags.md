# Remove git tags

## Locally

```bash 
git tag | xargs git tag -d
```

## On the remote repository

```bash 
git tag -l | xargs -n 1 git push --delete origin
```

---

#CommandLine #Git