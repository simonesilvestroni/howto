# Jekyll body class

We call liquid tags in the class for `body`, which we can use later in the theme phase. Particularly useful is the fact `page.title` can be printed as a class, so to potentially target single posts or pages with CSS.

```
<body class="layout-{{ page.layout }}{% if page.title %}  {{ page.title | slugify }}{% endif %}">
```

---

#Jekyll