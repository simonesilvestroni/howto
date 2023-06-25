# Copy and paste using the clipboard

```bash
# copies the directory listing
ls -l | pbcopy
```

```bash
# get clipboard lines containing foo and save them in a_file
pbpaste | grep foo > a_file
```

---

#Bash #CommandLine #macOS