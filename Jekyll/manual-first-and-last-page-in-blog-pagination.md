# Jekyll manual first and last page in blog pagination

The Jekyll plugin `paginate` v1.1 (the one whitelisted on GitHub Pages), doesn't support first/last URLs. Therefore, we created it manually.

```
<nav class="nav nav-paginator">
  {%- assign lastPage = paginator.total_pages -%}
  {%- assign secondToLast = lastPage | minus: 1 -%}
  {%- assign firstPage = 1 -%}
  {%- assign secondPage = firstPage | plus: 1 -%}
  {%- unless paginator.page == firstPage %}
  <a href="{{ site.url }}/blog/" class="pagination pagination-first">&#8676; First</a>
  {%- endunless -%}
  {%- if paginator.previous_page %}{%- unless paginator.page == secondPage %}
  <a href="{{ site.baseurl }}{{ paginator.previous_page_path }}" class="pagination pagination-previous">&larr; Previous</a>
  {%- endunless -%}
  {%- endif %}
  <span class="pagination pagination-counter">Page: <strong>{{ paginator.page }} of {{ paginator.total_pages }}</strong></span>
  {% if paginator.next_page -%}{%- unless paginator.page == secondToLast -%}
  <a href="{{ site.baseurl }}{{ paginator.next_page_path }}" class="pagination pagination-next">Next &rarr;</a>
  {% endunless -%}{%- endif -%}
  {%- unless paginator.page == lastPage -%}
  <a href="{{ site.url }}/{{ page.title | slugify }}/page/{{ paginator.total_pages }}/" class="pagination pagination-last">Last &#8677;</a>
  {% endunless -%}
</nav>
```

To better explain:

- We don't need "first" if we are on page 1.
- We don't need "previous" if we are on page 2 (since "first" would already suffice in that case).
- We don't need "next" if we are on the second to last page (since "last" would already suffice in that case).
- Similarly, we don't need "last" if we are on the last page.

---

#Jekyll