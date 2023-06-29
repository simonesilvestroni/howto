# Ruby on Mojave

## Install `rbenv`

Using Mac Ports:

```bash
sudo port install rbenv ruby-build
```

## Add `rbenv` to bash so that it loads every time you open a terminal

```bash
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile

source ~/.bash_profile
```

## Install Ruby

Run `rbenv versions` to see available Ruby versions, and `rbenv version` to see the current version being used.

Use `rbenv install --list` to list all installable versions.

```bash
rbenv install 3.1.3
```

## Set Ruby version

```bash
rbenv global 3.1.3
```

## Confirm

```bash
ruby -v
```

> **`NOTE`**
>
> The plugin `rbenv-bundler` makes it possible to not have to type `bundle exec` in front of every command. This can be installed with `sudo port install rbenv-bundler`.

---

#macOS #Bash #CommandLine