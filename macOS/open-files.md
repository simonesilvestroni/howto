# Open files and who's writing on disk

Discover what files are being opened, as they're being opened:

```bash
sudo fs_usage -e -f filesystem|grep -v CACHE_HIT|grep -v grep|grep open
```

Or who's writing on the disk:

```bash
sudo fs_usage -e -f filesystem|grep -v CACHE_HIT|grep -v grep|grep write
```

---

#Bash #CommandLine #macOS