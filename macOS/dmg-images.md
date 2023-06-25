# DMG images

## Create a DMG image

```bash
hdiutil create -format UDZO -srcfolder folder_to_compress archive_name.dmg
```

## Mount a DMG image

```bash
hdiutil attach archive_name.dmg
```

## View a DMG image

```bash
ls -lah /Volumes/archive_name/
```

## Eject a DMG image

```bash
hdiutil eject /Volumes/archive_name/
```

---

#macOS #Bash #CommandLine