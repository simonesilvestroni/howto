# Jekyll collections

Create a `portfolio` collection in `_config.yml`:

```
collections:
  portfolio:
    output: true
    permalink: /portfolio/:path/
```

- **Filesystem**: add a folder called `_portfolio` containing the single portfolio posts.
- Create a `for` cycle in `portfolio.html`, or anywhere it’s needed.

Since the permalinks are set in `config.yml`, I don't have to worry about the items being in different folders. I can decide to store them as I wish locally.

---

#Jekyll