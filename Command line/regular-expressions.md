# Regular expressions

To test and action a regex, go to [https://regex101.com/](https://regex101.com/) and either choose **Match** or **Substitution** from the sidebar on the left.

## Remove everything inside parenthesis:

```bash
\([^\)]*\)*
```

## Remove everything after a certain character

For example, remove the content after the forward slash:

```
trello/">TRELLO</a>
```

Regex to be used:

```bash
\/.*$
```

Result:

```
trello
```

## Remove return caret:

`\n`

---

#Bash #CommandLine #RegEx