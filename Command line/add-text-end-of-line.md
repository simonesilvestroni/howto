# Add text at the end of each line

`myfile.txt` contains:

```
india
sudan
japan
france
```

I want to add `| COUNTRY` at the end of each line. Use `awk` to print the line plus the given text, and pipe to a new text file:

```bash
awk '{print $0, "| COUNTRY"}' myfile.txt > myNEWfile.txt
india | COUNTRY
sudan | COUNTRY
japan | COUNTRY
france | COUNTRY
```

---

#Bash #CommandLine