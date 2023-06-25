# vi commands

## Command mode (case sensitive)

Move the cursor with arrow keys; if there aren't any arrow keys, use `j`,`k`,`h`,`l`

```bash
i - change to insert mode (before cursor)
a - change to insert mode (after cursor)
A - change to insert mode (at end of line)
r - replace one character
R - overwrite text
x - delete one character
dd - delete one line
yy - yank line (copy)
p - paste deleted or yanked text after cursor
P - paste deleted or yanked text before cursor
G - go to end of the file
1G - go to top of the file
$ - go to the end of the line
J - merge next line with this one
/ - search
n - Search for next instance of string
N - Search for previous instance of string
:wq - write file and quit
:q! - quit without saving
%s/old/new/g - substitute; replace "old" with "new" on all
lines
:g/pattern/d - delete all lines that match the pattern
```

## Insert mode

```bash
ESC - change to command mode
any text typed is entered at the cursor
u - Undo
```

---

#Bash #CommandLine