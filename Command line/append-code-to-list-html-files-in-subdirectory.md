# Append code to a list of .html files in a subdirectory

```bash
find . -type f -name "*.html" -exec sh -c 'cat somecode.txt >> "$1"' -- {} \;
```

The command will find, per the example, all the `.html` files inside the current directory (and below), appending the code found inside `somecode.txt`.

---

#Bash #CommandLine