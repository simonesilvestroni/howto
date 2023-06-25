# Visual Studio

## List all the installed local extensions

```bash
code --list-extensions
```

## List all the installed local extensions + output the command to install them on another machine

```bash
code --list-extensions | xargs -L 1 echo code --install-extension
```

## Local preferences storage

```bash
~/Library/Application Support/Code/User/
```

## Local extensions storage

```bash
~/.vscode/extensions
```

## Sync the color theme with macOS light/dark scheme

Search for this in preferences:

```bash
window.autoDetectColorScheme
```

Activate it and choose a default light/dark set of themes.

---

#CodeEditor