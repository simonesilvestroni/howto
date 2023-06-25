# Convert rtf to txt

```bash
find . -name \*.rtf -print0 | xargs -0 textutil -convert txt
```

---

#macOS #Bash #CommandLine