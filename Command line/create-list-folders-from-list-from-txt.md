# Create a list of folders following a list from a `.txt`

```bash
xargs -tI % mkdir % < names.txt
```

`-I` tells xargs to run a command for each line from STDIN. In this case, STDIN comes from reading the names.txt file with `< names.txt`.

`%` is a replacement string that xargs uses to as a placeholder for a line from the file. This means that everywhere `xargs` sees `%` in the command, `%` is replaced by a line from the file.

`-t` causes `xargs` to print each command before it's executed. It's not necessary, but it can be helpful for more complicated problems.

## Create an HTML file into a list of directories

```bash
find . -type d | xargs  -I '{}' touch '{}/index.html'
```

It finds all **directories** starting from the current directory and below. Pipes the result from `find` to use `xargs` to run `touch` replacing `{}` with the directory name passed from the previous command so you get `touch ./my/dir/path/index.html`.

---

#Bash #CommandLine