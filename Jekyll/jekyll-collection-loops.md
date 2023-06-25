# Jekyll collections loops

```liquid
{% for collection in site.collections%}
 Collection name: {{collection.label}} 
 Relative path to the collection's source directory: {{collection.relative_directory }}
 Full path to the collection's directory: {{collection.directory}}
 Output collection files as individual files?: {{collection.output}}
 {% for doc in collection.docs%}
  {{doc.title}}
  {{doc.slug}}
 {% endfor %}
{% endfor %}
```

---

```liquid
{% for collection in site.collections %}
<h4>Collection {{forloop.index}}</h4>
<dl>
{% for doc in collection.docs %}
<dt>Path</dt><dd>{{doc.path}}</dd>
<dt>Relative_path</dt><dd> {{doc.relative_path}}</dd>
<dt>Collection</dt><dd> {{doc.collection}}</dd>
<dt>Date</dt><dd> {{doc.date}}</dd>
{% endfor %}
</dl>
<hr>
{% endfor %}
```

---

#Jekyll