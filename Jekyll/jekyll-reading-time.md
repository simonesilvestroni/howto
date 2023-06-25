# Jekyll reading time

Include the functionality (average read per minute, per average user):

```
<span class="reading-time" title="Estimated read time">Reading time:
  {% assign words = content | number_of_words -%}
  {%- if words < 360 -%}
    1 min
  {%- else -%}
    {{ words | divided_by:180 }} mins
  {%- endif %}
</span>
```

---

#Jekyll