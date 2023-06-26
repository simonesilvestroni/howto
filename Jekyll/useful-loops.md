# Jekyll loops

## All pages

```liquid
{% assign pages = site.pages | where_exp: "item", "item.title" %}
{% for page in pages %}
  title: {{page.title}}
{% endfor %}
```

## All posts

```liquid
{% assign posts = site.posts %}
{% for posts in posts %}
  title: {{posts.title}}
{% endfor %}
```

## All pages and posts

```liquid
{% assign pagesAndPosts = pages | concat: posts %}
{% for pageAndPost in pagesAndPosts %}
  title: {{pageAndPost.title}}
{% endfor %}
```

---

#Jekyll