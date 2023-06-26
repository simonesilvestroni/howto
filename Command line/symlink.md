# Symlink

> **`TIP`**
> 
> You can drag a folder onto the Terminal after the typed command instead of typing the entire path.

## Case 1: move a large folder to an external hard drive

> **`EXAMPLE`**
> 
> I want to move my Logic sound library to an external SSD.

1. Copy or move the entire sound library folder from the internal HD (`/Library/Application Support/Logic/`) to the new intended location (`/Volumes/EXTERNALHD/`).
2. Once completed, the new folder will be `/Volumes/EXTERNALHD/Logic/`.
2. Delete the original folder if you copied instead of moving.
3. Terminal: go the the **container** (up one level) of the original folder.

```
cd “/Library/Application Support/“
ln -s /Volumes/EXTERNALHD/Logic/
```

By doing so, now there will be a `Logic` “shortcut” inside `‌/Library/Application Support/`.

## Case 2: create a symlink from a folder to another one

> **`EXAMPLE`**
> 
> I want to have a symlink of my Picture folder in my Documents folder.

```
cd ~/Documents
ln -s ~/Pictures
```

Open Documents: there should be a “shortcut” of Pictures inside.

---

#Bash #CommandLine