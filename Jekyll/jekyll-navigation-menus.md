# Jekyll navigation menus

Create a `_data` folder at the root level. Put the navigation YAML file inside. For example:

- `nav-site.yml`
- `nav-social.yml`
- etc

Each file is a structured data, with the required elements needed to print in any page/post either or both the nav title and nav link.

## `nav-site.yml`

```
- name: Home
  link: /
- name: About
  link: /about/
- name: Portfolio
  link: /portfolio/
- name: Blog
  link: /blog/
- name: Contacts
  link: /contacts/
- name: Search
  link: /search/
```

## `nav-social.yml`

```
- name: LinkedIn
  link: https://www.linkedin.com/in/personal-url/
- name: GitHub
  link: https://github.com/personal-url
- name: Flickr
  link: https://www.flickr.com/photos/personal-url/
```

## Include a navigation menu in a page/post

Create a file under `_includes` and call it `navigation-social.html`:

```
<nav>
  <ul>
    {% for item in site.data.nav-social -%}
    <li><a href="{{ item.link }}" title="Visit my {{ item.name }} profile">{{ item.name }}</a></li>
    {% endfor -%}
  </ul>
</nav>
```

At this point, include it in any post or page:

`{%- include navigation-social.html %}`

## Conclusion

The same method can be applied to each navigation menu.

---

#Jekyll