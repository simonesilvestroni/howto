# Jekyll archive without plugins

Create a collection:

```ruby
collections:
  my_categories:
    output: true
    permalink: /category/:name/
```

Add taxonomy to posts/pages:

```yaml
---
layout: default
categories: food
tags: Food
---
```

The magic comes from `output: true` which causes jekyll to generate pages according to their **permalink value**.

Add some template logic on top of the post layout:

```liquid
{% assign category = site.my_categories | where: "categories", post.category %}
{% assign category = category[0] %}
{% if category %}
    {% capture category_content %}<a class="label" href="{{ category.url }}">{{ category.name }}</a>{% endcapture %}
{% endif %}
```

Place the generated taxonomy content wherever you like inside the post layout:

```html
<p class="post-meta">{{ category_content }}</p>
```

---

From: [https://www.minddust.com/post/alternative-tags-and-categories-on-github-pages/](https://www.minddust.com/post/alternative-tags-and-categories-on-github-pages/)

Example **post**: [https://github.com/minddust/minddust.github.io/blob/master/_posts/2014-04-11-opensourced-minddust-com.md](https://github.com/minddust/minddust.github.io/blob/master/_posts/2014-04-11-opensourced-minddust-com.md)

Example page **blog by tag**: [https://github.com/minddust/minddust.github.io/blob/master/_layouts/blog_by_tag.html](https://github.com/minddust/minddust.github.io/blob/master/_layouts/blog_by_tag.html)

Example page **blog by category**: [https://github.com/minddust/minddust.github.io/blob/master/_layouts/blog_by_category.html](https://github.com/minddust/minddust.github.io/blob/master/_layouts/blog_by_category.html)

Example post layout **containing the logic**: [https://github.com/minddust/minddust.github.io/blob/master/_layouts/post.html](https://github.com/minddust/minddust.github.io/blob/master/_layouts/post.html)

---

#Jekyll