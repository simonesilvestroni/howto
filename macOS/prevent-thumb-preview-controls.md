# Prevent thumb preview controls from showing

To disable movie, PDF, and other useless previews, but still maintain the image on the icon, use this from Terminal:

```bash
defaults write com.apple.finder QLInlinePreviewMinimumSupportedSize -int 512
```

Relaunch the Finder.

---

#macOS #Bash #CommandLine