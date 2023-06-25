# Time Machine

## Delete Time Machine backup

```bash
sudo /System/Library/Extensions/TMSafetyNet.kext/Helpers/bypass rm -r /Volumes/TIME/Backups.backupdb/
```

## Disable local Time Machine

```bash
sudo tmutil disablelocal
```

## Stop Time Machine from asking new disks

```bash
defaults write com.apple.TimeMachine DoNotOfferNewDisksForBackup -bool TRUE
```

---

#macOS #Bash #CommandLine #backup