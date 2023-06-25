# Install Ruby on Mojave

## Install Rbenv

`brew install rbenv ruby-build`

## Add rbenv to bash so that it loads every time you open a terminal

```bash
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile

source ~/.bash_profile
```

## Install Ruby

rbenv install 3.2.1

## Set Ruby version

```bash
rbenv global 3.2.1
```

## Confirm

```bash
ruby -v
```

---

#macOS #Bash #CommandLine