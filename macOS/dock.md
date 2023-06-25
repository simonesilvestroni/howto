# Dock

## Reduce the Dock’s hiding animation

```bash
defaults write com.apple.dock autohide-time-modifier -float 0.12;killall Dock
```

## Restore the default Dock’s hiding animation

```bash
defaults delete com.apple.dock autohide-time-modifier;killall Dock
```

---

#macOS #Bash #CommandLine