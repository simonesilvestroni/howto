# Spotlight: reset index

Turn Spotlight **off**:

```bash
sudo mdutil -a -i off
```

Then:

```bash
sudo mdutil -E /
sudo rm -Rf /var/folders/*
```

After a reboot, turn Spotlight **back on**:

```bash
sudo mdutil -a -i on
```

See the progress:

```bash
sudo opensnoop -n mdworker
```

Turn indexing **off** for pure backup disks:

```bash
sudo mdutil -i off /Mountpoint/Volumename
```

---

#macOS #Bash #CommandLine