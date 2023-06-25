# Liquid logic to gather all the collections together

```ruby
{%- assign collectionname1 = site.collection1 | reverse -%}
{%- assign collectionname2 = site.collection2 | reverse -%}
{%- assign collectionname3 = site.collection3 | reverse -%}
{%- assign = collections = collectionname1 | concat: collectionname2 | concat: collectionname3 -%}
{%- assign sortedcollections = collections | sort: 'date' | reverse -%}
```

---

#Jekyll