# `tail`

Prints last `n` lines of each file to standard output. With more than one file, precede each with a header giving the file name.

```bash
tail [-f|-r] [-b number|-c number|-n number|-number] [file ...]
```

Examples:

```bash
tail -F /path-to-your-file/file.log
tail -500 foo
```

---

#Bash #CommandLine