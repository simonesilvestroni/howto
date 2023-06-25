# Iterate through different loops

> **`EXAMPLE`**
> 
> I have a section in my homepage called *Case Studies*, where I want to show the latest post tagged with `case study` but at the same time I want to show the latest case study for the category `web design` and the latest for the category `music release`.

## Solution

First, assign a variable `sorted-web` to the first logic (`case study` + `web design`), then do the same for the second logic (`case study` + `music release`). Finally, concatenate both within a third variable `sorted-posts`. 

That **third variable** is the filter we’re going to use for our loop (limited to `2` because I want to show one post per each case).

```liquid
{% assign sorted-web = site.posts | where: "categories","Web design" | where: "tags","case study" %}

{% assign sorted-audio = site.posts | where: "categories","Music release" | where: "tags","case study" %}

{% assign sorted-posts = sorted-web | concat: sorted-audio  %}

{% for post in sorted-posts limit: 2 %}
    do your stuff
{% endfor %}
```

---

#Jekyll