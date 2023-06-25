# List users

## List all users and accounts

```bash
dscl . list /Users
```

## Show user accounts only

```bash
dscl . list /Users | grep -v '_'
```

---

#macOS #Bash #CommandLine