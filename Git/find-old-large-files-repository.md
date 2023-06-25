# Find old large files in git repository

> **`NOTE`**
> 
> Requires `brew install coreutils`

```bash
git rev-list --objects --all |
  git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' |
  sed -n 's/^blob //p' |
  sort --numeric-sort --key=2 |
  gcut -c 1-12,41- |
  $(command -v gnumfmt || echo gnumfmt) --field=2 --to=iec-i --suffix=B --padding=7 --round=nearest
```

## Filtering

To achieve _further filtering_, insert the following line _before_ the `sort` line: to **exclude files that are present in `HEAD`**, insert:

```bash
grep -vF --file=<(git ls-tree -r HEAD | awk '{print $3}') |
```

[Source](https://stackoverflow.com/questions/10622179/how-to-find-identify-large-commits-in-git-history "Read more on Stack Overflow")

---

#CommandLine #Git