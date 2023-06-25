# Find

## From the root

```bash
find / -name '*.mov' -print
```

## From the current directory

```bash
find . -name '*.mov' -print
```

## Recursive

### Directories

```bash
find . -type d -exec chmod 755 {} \;
```

### Files

```bash
find . -type f -exec chmod 644 {} \;
```

## Find and remove recursively directories

```bash
find . -type d -name '.svn' -print0 | xargs -0 rm -rv
```

## Find *.txt and replace with* .md

```bash
for txtFile in  $(find . -type f -name '*.txt' -print); do mv "$txtFile" "${txtFile%.*}.md" ; done
```

---

#Bash #CommandLine