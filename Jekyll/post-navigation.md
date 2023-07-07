# Jekyll post navigation

The crucial bit:

```
{% if page.previous.url %}
<span>OLDER</span>
<a href="{{ site.url }}{{ page.previous.url }}">{{ page.previous.title }}</a>
{% endif %}

{% if page.next.url %}
<span>NEWER</span>
<a href="{{ site.url }}{{ page.next.url }}">{{ page.next.title }}</a>
{% endif %}
```

Add the appropriate semantic tags, and visually style as needed.

## Example for a 2-column layout

Relevant markup:

```
<div class="pagination">
  {% if page.previous.url %}
  <p>
    <span>&larr; <strong>Older post</strong></span>
    <a href="{{ site.url }}{{ page.previous.url }}">{{ page.previous.title }}</a>    
  </p>
  {% endif %}
  {% if page.next.url %}
  <p>
    <span><strong>Newer post</strong> &rarr;</span>
    <a href="{{ site.url }}{{ page.next.url }}">{{ page.next.title }}</a>    
  </p>
  {% endif %}
</div>
```

Related CSS styles:

```css
.pagination {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  margin-top: 5rem;
}
.pagination p {
  width: 48.5%;
}
.pagination span {
  display: block;
  font-size: smaller;
}
```