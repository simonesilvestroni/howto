# Macports

## Cleanup

```
sudo port -f clean --all all
sudo port -f uninstall inactive
```

If you can't wait for the clean one to run in the background, there are a few commands you can run manually and faster.

Remove leftover build files (this is done automatically by default):

```
sudo rm -rf /opt/local/var/macports/build/*
```

Remove download files:

```
sudo rm -rf /opt/local/var/macports/distfiles/*
```

Remove archives (these aren't created by default):

```
sudo rm -rf /opt/local/var/macports/packages/*
```

## List installed

```
port installed
```

## Update installed

```
sudo port selfupdate
```

## Upgrade installed ports

```
sudo port upgrade outdated
```

## From Homebrew to Macports

- Have X-Code devtools installed.
- Download and run the MacPorts installer for your macOS version from [macports.org](https://www.macports.org/install.php)

### Switch packages from Homebrew to MacPorts

- See what you have in Homebrew with `brew leaves --installed-on-request | xargs -n1 brew desc`
- Remove `[thing]` from Homebrew with `brew remove thing` 
- Add `[thing]` with MacPorts with `sudo port install thing` 
- Repeat

Most packages have exactly the same name on both platforms, but when in doubt you can run port search `[thing]` or search in the browser at [ports.macports.org](https://ports.macports.org).

---

#macOS #Bash #CommandLine
