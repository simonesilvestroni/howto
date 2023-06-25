# Reset all changes after last commit

## First, reset any changes

This will undo any changes you've made to tracked files and restore deleted files:

```bash
git reset HEAD --hard
```

## Second, remove new files

This will delete any new files that were added since the last commit:

```bash
git clean -fd
```

Files that are not tracked due to `.gitignore` are preserved; they will not be removed

> **`WARNING`**
> 
> Using `-x` instead of `-fd` *would* delete ignored files.  You probably don't want to do this.

---

#CommandLine #Git