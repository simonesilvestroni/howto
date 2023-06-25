# `rsync` after interrupted `scp`

```bash
rsync -rvz -e 'ssh' --partial --progress ~/my-local-dir/ remoteUser@remoteURL:/remote/path/
```

---

#Bash #CommandLine