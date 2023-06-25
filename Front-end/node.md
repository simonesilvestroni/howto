# Node and Npm

> **`RESOURCE`**
> 
> Beginners’ guide: [https://nodesource.com/blog/an-absolute-beginners-guide-to-using-npm/](https://nodesource.com/blog/an-absolute-beginners-guide-to-using-npm/)

Use `nvm`, a package manager for **node**, to install and manage both `node` and `npm` locally.

## Install `nvm`

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

Close and reopen the Terminal upon successful installation.

## Check `bash_profile`

Check that the installer added the following at the bottom:

```bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
```

## Download, compile and install Node

To download, compile, and install the latest release of node, do this:

```bash
nvm install node # "node" is an alias for the latest version
```

To install a specific version of node:

```bash
nvm install 14.7.0 # or 16.3.0, 12.22.1, etc
```

The first version installed becomes the default. New shells will start with the default version of node (e.g., `nvm alias default`).

You can list available versions using `ls-remote`:

```bash
nvm ls-remote
```

And then in any new shell just use the installed version:

```bash
nvm use node
```

Or you can just run it:

```bash
nvm run node --version
```

## `npm`

It is installed with `node`.

## Environment variables

`nvm` exposes the following environment variables:

```
NVM_DIR - nvm's installation directory.
NVM_BIN - where node, npm, and global packages for the active version of node are installed.
NVM_INC - node's include file directory (useful for building C/C++ addons for node).
NVM_CD_FLAGS - used to maintain compatibility with zsh.
NVM_RC_VERSION - version from .nvmrc file if being used.
```

Additionally, nvm modifies `PATH`, and, if present, `MANPATH` and `NODE_PATH` when changing versions.

> **`READ MORE`**
> 
> [https://github.com/nvm-sh/nvm#usage](https://github.com/nvm-sh/nvm#usage)

---

#macOS #Bash #CommandLine