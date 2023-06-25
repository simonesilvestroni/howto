# Rename a file list based on a `.txt` file

Notes:

- do all the commands together, separated with `;`
- replace `XXX` with the suffix

```bash
for file in *.mp3; do read line; mv -v "${file}" "${line}.XXX"; done < list
```

---

#Bash #CommandLine