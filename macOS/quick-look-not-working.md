# Quick look stops working

If image thumbnails don't show up or stopped showing up in Finder when in _icons view_, do the following:

- Open Activity Monitor
- Look for the process `com.apple.quicklook.ThumbnailsAgent`
- Force quit the process
- Relaunch Finder

If it doesn't work, try:

```bash
qlmanage -r cache
```

---

#macOS #Bash #CommandLine