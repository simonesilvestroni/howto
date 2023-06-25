# Remove all the Finder personalised window views

```bash
sudo find / -name ".DS_Store" -exec rm {} \;
```

Restart, then open a window, set the view preferences and check the option `set as default`.

---

#macOS #Bash #CommandLine