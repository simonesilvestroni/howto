# Change permissions for files and directories

```bash
find . -type d -exec chmod 755 {} ;
find . -type f -exec chmod 644 {} ; 
chmod 440 wp-config.php
```

---

#Bash #CommandLine