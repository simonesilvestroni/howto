# Jekyll excerpt

- Set `excerpt_separator` globally in `_config.yml`, to be: `<!--more-->`.
- Apply `{{ post.excerpt }}` in the blogroll template (`/blog/index.html`) in place of `{{ post.content }}`, or where it's needed (such as a category or tag archive page).
- Use `<!--more-->` in the actual posts to tell Jekyll where it should _cut_ the post for the excerpt content.

---

#Jekyll