# Remove multiple entries in `open with` menu

```bash
/System/Library/Frameworks/CoreServices.framework/Frameworks/LaunchServices.framework/Support/lsregister -kill -r -domain local -domain system -domain user;killall Finder
```

---

#macOS #Bash #CommandLine