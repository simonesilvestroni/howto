# SSH

## keygen

```bash
ssh-keygen -t rsa -C "yourname@yourdomain.ext"
```

## Copy public key

```bash
pbcopy < ~/.ssh/id_rsa.pub` `pbpaste > ~/clipboard.text
```

## `ssh` to remote server

```bash
ssh -p $port $user@$serverIP/URL
```

## Persist `ssh` agent in macOS keychain

```bash
ssh-add -K /path/to/key
```

## Forgotten SSH passphrase

- In Keychain Access, search for SSH.
- Double click on the entry for your SSH key to open a new dialog box.
- In the lower-left corner, select Show password. 

---

#Bash #CommandLine