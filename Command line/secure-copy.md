# Secure copy

## `scp` (secure copy) file from remote to local

I’m in the correct local directory where I want the file to be downloaded:

```bash
scp -P 18765 -r user@server:/remote/dir/public_html/file.ext ./
```

## `scp` entire site or directory from remote to local

I’m in the correct local directory where I want the remote folder to be downloaded:

```bash
scp -r user@server:/remote/dir/public_html/ /Users/user/Sites/MyLocalCopy
```

## `scp` from local to remote

The local file is in my home directory.

```bash
scp -P0000 ~/my-local-file user@server:/remote/dir/public_html/my-remote-file.ext
```

## `scp` from local to remote for directories (recursively)

```bash
scp -P0000 -r user@server:/remote/dir/public_html/ /Volumes/VOLUMENAME/DIR/
```

---

#Bash #CommandLine