# Getting started with Jekyll

> **`WARNING`**
> 
> This guide is likely obsolete in several parts.

## Set up

### Prerequisites

#### macOS specific requirements

1. Install command line tools:

    **`xcode-select --install`**

2. Set **SDKROOT** (only macOS Catalina or later).

    Starting on macOS Catalina (10.15) the headers used for Ruby have been moved from their previous location which results in some gems, including Jekyll to fail installation. This can be solved by setting `SDKROOT` in your shell configuration to the value provided by `xcrun`:

    **`export SDKROOT=$(xcrun --show-sdk-path)`**

Jekyll is a **Ruby Gem** that can be installed on most systems. It requires:

1. Ruby version 2.4.0 or higher, including all development headers (check your Ruby version using **`ruby -v`**).
2. RubyGems (check your Gems version using **`gem -v`**).
3. GCC and Make (check versions using **`gcc -v`**,**`g++ -v`**, and **`make -v`**).

### Install Ruby on macos

https://mac.install.guide/ruby/index.html

### Install the jekyll and bundler gems (predefinite gem theme)

**`sudo gem install jekyll bundler`**

- Create a new Jekyll site at **`./mywebsite`**:

    **`jekyll new mywebsite`**

- Change into your new directory:

    **`cd mywebsite`**

- Build the site and make it available on a local server:

    **`sudo bundle exec jekyll serve`**

- Browse to **`http://localhost:4000`**

    Pass the **`--livereload`** option to automatically refresh the page with each change you make to the source files:

    **`bundle exec jekyll serve --livereload`**.

## Install Jekyll step-by-step

> This procedure builds a first Jekyll site from scratch without relying on the default gem-based theme.

With Ruby installed, install Jekyll from the terminal:

**`sudo gem install jekyll bundler`**

Create a new `Gemfile` to list your project’s dependencies:

**`bundle init`**

Edit the `Gemfile` in a text editor and add jekyll as a dependency:

```
gem "jekyll"
```

Run **`bundle`** to install jekyll for your project.

You can now prefix all jekyll commands listed in this tutorial with **`bundle exec`** to make sure you use the jekyll version defined in your Gemfile.

Ruby 3.0 doesn't come with webrick anymore (necessary for livereload), so:

```gem install webrick```

Then, in the website directory:

```bundle add webrick```

### Create a site

Create a new directory for your site and name it whatever you want. Through the rest of this tutorial we’ll refer to this directory as **root**.

You can also initialize a Git repository here.

One of the great things about Jekyll is there’s no database. All content and site structure are files that a Git repository can version. Using a repository is optional but is recommended.

Let’s add your first file. Create **`index.html`** in root with the following content:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```

#### Build

Since Jekyll is a static site generator, it has to build the site before we can view it. Run either of the following commands to build your site:

- **`jekyll build`** - Builds the site and outputs a static site to a directory called `_site`.
- **`jekyll serve`** - Does jekyll build and runs it on a local web server at `http://localhost:4000`, rebuilding the site any time you make a change.

> To force the browser to refresh with every change, use **`jekyll serve --livereload`**.

Go to http://localhost:4000 in your browser. You should see “Hello World!”.

At this point, the only thing that happened was that Jekyll copied an HTML file from one place to another.

> **`TIP`**
> 
> More info about installing Jekyll on macOS [at this page](https://jekyllrb.com/docs/installation/macos/).

---

#### Liquid

Liquid is a **templating language** which has three main components:

- objects
- tags
- filters

##### OBJECTS

Objects tell Liquid to output predefined variables as content on a page. Use double curly braces for objects: **`{% raw %}{{ and }}{% endraw %}`**.

For example, **`{{ page.title }}`** displays the `page.title variable`.

##### TAGS

Tags define the logic and control flow for templates. Use curly braces and percent signs for tags: **`{% raw %}{% and %}{% endraw %}`**.

For example:

```html
{% if page.show_sidebar %}
  <div class="sidebar">
    sidebar content
  </div>
{% endif %}
```

This displays the sidebar if the value of the `show_sidebar` page variable is true.

Learn more about the tags available in Jekyll [here](https://jekyllrb.com/docs/liquid/tags/).

##### FILTERS

Filters change the output of a Liquid object. They are used within an output and are separated by a `|`.

For example:

**`{{ "hi" | capitalize }}`**

This displays Hi instead of hi.

[Learn more about the filters](https://jekyllrb.com/docs/liquid/filters/) available.

##### USE LIQUID

Now, use Liquid to make your Hello World! text from Setup lowercase:

```liquid
<h1>{{ "Hello World!" | downcase }}</h1>
```

To make Jekyll process your changes, add **front matter** to the top of the page:

```liquid
---
# front matter tells Jekyll to process Liquid
---
```

Your HTML document should look like this:

```html
---
---

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Home</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```

When you reload your browser, you should see **hello world!**.

Much of Jekyll’s power comes from combining Liquid with other features. Add [frontmatter](https://jekyllrb.com/docs/step-by-step/03-front-matter/) to pages to make Jekyll process the Liquid on those pages.

##### FRONT MATTER

Front matter is a snippet of [**YAML**](http://yaml.org/) placed between two triple-dashed lines at the start of a file.

You can use front matter to set variables for the page:

```liquid
---
my_number: 5
---
```

You can call front matter variables in Liquid using the **`page`** variable. For example, to output the value of the `my_number` variable above:

**`{{ page.my_number }}`**

###### USE FRONT MATTER

Change the **`<title>`** on your site to use front matter:

```html
---
title: Home
---
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    <h1>{{ "Hello World!" | downcase }}</h1>
  </body>
</html>
```

You **must include** front matter on the page for Jekyll to process any Liquid tags on it.

To make Jekyll process a page without defining variables in the front matter, use:

```liquid
---
---
```

##### LAYOUTS

Jekyll **supports Markdown in addition to HTML** when building pages. Markdown is a great choice for pages with a simple content structure (just paragraphs, headings and images), as it’s less verbose than raw HTML.

Create a new Markdown file named **`about.md`** in your site’s root folder.

You could copy the contents of **`index`** and modify it for the About page. However, this creates duplicate code that has to be customized for each new page you add to your site.

For example, adding a new stylesheet to your site would involve adding the link to the stylesheet to the **`<head>`** of each page. For sites with many pages, this is a waste of time.

###### CREATING A LAYOUT

Layouts are templates that can be used by any page in your site and wrap around page content. They are stored in a directory called **`_layouts`**.

Create the **`_layouts`** directory in your site’s root folder and create a new **`default.html`** file with the following content:

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {{ content }}
  </body>
</html>
```

This HTML is almost identical to **`index.html`** except there’s no front matter and the content of the page is replaced by a **`content`** variable.

**`content`** is a special variable that returns the rendered content of the page on which it’s called.

###### USE LAYOUTS

To make **`index.html`** use your new layout, set the **`layout`** variable in the front matter. The file should look like this:

```liquid
---
layout: default
title: Home
---
<h1>{{ "Hello World!" | downcase }}</h1>
```

When you reload the site, the output remains the same.

Since the layout wraps around the content on the page, you can call front matter like **`page`** in the layout file. When you apply the layout to a page, it uses the front matter on that page.

###### BUILD THE ABOUT PAGE

Add the following to **`about.md`** to use your new layout in the About page:

```liquid
---
layout: default
title: About
---
# About page

This page tells you a little bit about me.
```

Open http://localhost:4000/about.html in your browser and view your new page.

##### INCLUDES

There’s still no way to navigate between pages.

**Navigation** should be on every page so adding it to your layout is the correct place to do this. Instead of adding it directly to the layout, let’s use this as an opportunity to learn about includes.

###### INCLUDE TAG

The **`include`** tag allows you to include content from another file stored in an **`_includes`** folder. Includes are useful for having a single source for source code that repeats around the site or for improving the readability.

Navigation source code can get complex, so sometimes it’s nice to move it into an include.
Include usagePermalink

Create a file for the navigation at **`_includes/navigation.html`** with the following content:

```html
<nav>
  <a href="/">Home</a>
  <a href="/about.html">About</a>
</nav>
```

Try using the include tag to add the navigation to **`_layouts/default.html`**:

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```

Open http://localhost:4000 in your browser and try switching between the pages.

###### CURRENT PAGE HIGHLIGHTING

Let’s take this a step further and highlight the current page in the navigation.

**`_includes/navigation.html`** needs to know the URL of the page it’s inserted into so it can add styling. Jekyll has useful [variables](https://jekyllrb.com/docs/variables/) available, one of which is **`page.url`**.

Using **`page.url`** you can check if each link is the current page and color it red if true:

```html
<nav>
  <a href="/" {% if page.url == "/" %}style="color: red;"{% endif %}>
    Home
  </a>
  <a href="/about.html" {% if page.url == "/about.html" %}style="color: red;"{% endif %}>
    About
  </a>
</nav>
```

Take a look at http://localhost:4000 and see your red link for the current page.

There’s still a lot of repetition here if you wanted to add a new item to the navigation or change the highlight color. In the next step we’ll address this.

##### DATA FILES

Jekyll supports loading data from YAML, JSON, and CSV files located in a **`_data`** directory. Data files are a great way to separate content from source code to make the site easier to maintain.

In this step you’ll store the contents of the navigation in a data file and then iterate over it in the navigation include.

###### DATA FILE USAGE

[YAML](http://yaml.org/) is a format that’s common in the Ruby ecosystem. You’ll use it to store an array of navigation items each with a name and link.

Create a data file for the navigation at **`_data/navigation.yml`** with the following:

```yml
- name: Home
  link: /
- name: About
  link: /about.html
```

Jekyll makes this data file available to you at **`site.data.navigation`**. Instead of outputting each link in **`_includes/navigation.html`**, now you can iterate over the data file instead:

```html
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}style="color: red;"{% endif %}>
      {{ item.name }}
    </a>
  {% endfor %}
</nav>
```

The output will be exactly the same. The difference is you’ve made it easier to add new navigation items and change the HTML structure.

What good is a site without CSS, JS and images? Let’s look at how to handle assets in Jekyll.

##### ASSETS

Using CSS, JS, images and other assets is straightforward with Jekyll. Place them in your site folder and they’ll copy across to the built site.

Jekyll sites often use this structure to keep assets organized:

```
.
├── assets
│   ├── css
│   ├── images
│   └── js
...
```

So, from your assets folder, create folders called css, images and js. Additionally, directly under the root create another folder called ‘_sass’, which you will need shortly.

###### SASS

Inlining the styles used in **`_includes/navigation.html`** (adding or configuring within the same file) is not a best practice. Instead, let’s style the current page by defining our first class in a new CSS file instead.

To do this, refer to the class (that you will configure in the next parts of this step) from within the **navigation.html** file by removing the code you added earlier (to color the current link red) and inserting the following code:

```html
<nav>
  {% for item in site.data.navigation %}
    <a href="{{ item.link }}" {% if page.url == item.link %}class="current"{% endif %}>{{ item.name }}}</a>
  {% endfor %}
</nav>
```

You could use a standard CSS file for styling, we’re going to take it a step further by using [Sass](https://sass-lang.com/). Sass is a fantastic extension to CSS baked right into Jekyll.

First create a Sass file at **`assets/css/styles.scss`** with the following content:

```liquid
---
---
@import "main";
```

The empty front matter at the top tells Jekyll it needs to process the file. The **`@import "main"`** tells Sass to look for a file called **`main.scss`** in the sass directory (**`_sass/`**) by default which you already created directly under the root folder of your website).

At this stage you’ll just have a main css file. For larger projects, this is a great way to keep your CSS organized.

Create the current class mentioned above in order to color the current link green. Create a Sass file at **`_sass/main.scss`** with the following content:

```css
.current {
  color: green;
}
```

You’ll need to reference the stylesheet in your layout.

Open **`_layouts/default.html`** and add the stylesheet to the **`<head>`**:

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{{ page.title }}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
  </head>
  <body>
    {% include navigation.html %}
    {{ content }}
  </body>
</html>
```

The **`styles.css`** referenced here is generated by Jekyll from the **`styles.scss`** you created earlier in **`assets/css/`**.

Load up http://localhost:4000 and check that the active link in the navigation is green.

##### BLOGGING

You might be wondering how you can have a blog without a database. In true Jekyll style, blogging is powered by text files only.

###### POSTS

Blog posts live in a folder called **`_posts`**. The filename for posts have a special format: the publish date, then a title, followed by an extension.

Create your first post at **`_posts/2018-08-20-bananas.md`** with the following content:

```liquid
---
layout: post
author: jill
---
A banana is an edible fruit – botanically a berry – produced by several kinds of large herbaceous flowering plants in the genus Musa.

In some countries, bananas used for cooking may be called "plantains", distinguishing them from dessert bananas. The fruit is variable in size, color, and firmness, but is usually elongated and curved, with soft flesh rich in starch covered with a rind, which may be green, yellow, red, purple, or brown when ripe.
```

This is like the **`about.md`** you created before except it has an author and a different layout. **`author`** is a custom variable, it’s not required and could have been named something like **`creator`**.

###### LAYOUT

The **`post`** layout doesn’t exist so you’ll need to create it at **`_layouts/post.html`** with the following content:

```liquid
---
layout: default
---
<h1>{{ page.title }}</h1>
<p>{{ page.date | date_to_string }} - {{ page.author }}</p>

{{ content }}
```

This is an example of layout inheritance. The post layout outputs the title, date, author and content body which is wrapped by the default layout.

Also note the **`date_to_string`** filter, this formats a date into a nicer format.

###### LIST POSTS

There’s currently no way to navigate to the blog post. Typically a blog has a page which lists all the posts, let’s do that next.

Jekyll makes posts available at **`site.posts`**.

Create **`blog.html`** in your root (**`/blog.html`**) with the following content:

```liquid
---
layout: default
title: Blog
---
<h1>Latest Posts</h1>

<ul>
  {% for post in site.posts %}
  <li>
    <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    {{ post.excerpt }}
  </li>
  {% endfor %}
</ul>
```

There’s a few things to note with this code:

- **`post.url`** is automatically set by Jekyll to the output path of the post.
- **`post.title`** is pulled from the post filename and can be overridden by setting **`title`** in front matter.
- **`post.excerpt`** is the first paragraph of content by default.

You also need a way to navigate to this page through the main navigation. Open **`_data/navigation.yml`** and add an entry for the blog page:

```yml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
```

###### MORE POSTS

A blog isn’t very exciting with a single post. Add a few more:

**`_posts/2018-08-21-apples.md`**:

```liquid
---
layout: post
author: jill
---
An apple is a sweet, edible fruit produced by an apple tree.

Apple trees are cultivated worldwide, and are the most widely grown species in the genus Malus. The tree originated in Central Asia, where its wild ancestor, Malus sieversii, is still found today. Apples have been grown for thousands of years in Asia and Europe, and were brought to North America by European colonists.
```

**`_posts/2018-08-22-kiwifruit.md`**:

```liquid
---
layout: post
author: ted
---
Kiwifruit (often abbreviated as kiwi), or Chinese gooseberry is the edible berry of several species of woody vines in the genus Actinidia.

The most common cultivar group of kiwifruit is oval, about the size of a large hen's egg (5–8 cm (2.0–3.1 in) in length and 4.5–5.5 cm (1.8–2.2 in) in diameter). It has a fibrous, dull greenish-brown skin and bright green or golden flesh with rows of tiny, black, edible seeds. The fruit has a soft texture, with a sweet and unique flavor.
```

Open http://localhost:4000 and have a look through your blog posts.

Next we’ll focus on creating a page for each post author.

##### COLLECTIONS

Let’s look at fleshing out authors so each author has their own page with a blurb and the posts they’ve published.

To do this you’ll use collections. Collections are similar to posts except the content doesn’t have to be grouped by date.

###### CONFIGURATION

To set up a collection you need to tell Jekyll about it. Jekyll configuration happens in a file called **`_config.yml`** (by default).

Create **`_config.yml`** in the root with the following:

```yml
collections:
  authors:
```

To (re)load the configuration, restart the jekyll server. Press `Ctrl+C` in your terminal to stop the server, and then **`jekyll serve`** to restart it.

###### ADD AUTHORS

Documents (the items in a collection) live in a folder in the root of the site named `_*collection_name*`. In this case, **`_authors`**.

Create a document for each author:

**`_authors/jill.md`**:

```liquid
---
short_name: jill
name: Jill Smith
position: Chief Editor
---
Jill is an avid fruit grower based in the south of France.
```

**`_authors/ted.md`**:

```liquid
---
short_name: ted
name: Ted Doe
position: Writer
---
Ted has been eating fruit since he was baby.
```

###### STAFF PAGE

Let’s add a page which lists all the authors on the site. Jekyll makes the collection available at **`site.authors`**.

Create **`staff.html`** and iterate over **`site.authors`** to output all the staff:

```liquid
---
layout: default
title: Staff
---
<h1>Staff</h1>
<ul>
  {% for author in site.authors %}
  <li>
    <h2>{{ author.name }}</h2>
    <h3>{{ author.position }}</h3>
    <p>{{ author.content | markdownify }}</p>
  </li>
  {% endfor %}
</ul>
```

Since the content is markdown, you need to run it through the **`markdownify`** filter. This happens automatically when outputting using **`{% raw %}{{ content }}{% endraw %}`** in a layout.

You also need a way to navigate to this page through the main navigation. Open **`_data/navigation.yml`** and add an entry for the staff page:

```yml
- name: Home
  link: /
- name: About
  link: /about.html
- name: Blog
  link: /blog.html
- name: Staff
  link: /staff.html
```

###### OUTPUT A PAGE

By default, collections do not output a page for documents. In this case we want each author to have their own page so let’s tweak the collection configuration.

Open **`_config.yml`** and add **`output: true`** to the author collection configuration:

```yml
collections:
  authors:
    output: true
```

Restart the jekyll server once more for the configuration changes to take effect.

You can link to the output page using **`author.url`**.

Add the link to the **`staff.html`** page:

```liquid
---
layout: default
title: Staff
---
<h1>Staff</h1>

<ul>
  {% for author in site.authors %}
    <li>
      <h2><a href="{{ author.url }}">{{ author.name }}</a></h2>
      <h3>{{ author.position }}</h3>
      <p>{{ author.content | markdownify }}</p>
    </li>
  {% endfor %}
</ul>
```

Just like posts you’ll need to create a layout for authors.

Create **`_layouts/author.html`** with the following content:

```liquid
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}
```

###### FRONT MATTER DEFAULTS

Now you need to configure the author documents to use the **`author`** layout. You could do this in the front matter like we have previously but that’s getting repetitive.

What you really want is all posts to automatically have the post layout, authors to have author and everything else to use the default.

You can achieve this by using [front matter defaults](https://jekyllrb.com/docs/configuration/front-matter-defaults/) in **`_config.yml`**. You set a scope of what the default applies to, then the default front matter you’d like.

Add defaults for layouts to your **`_config.yml`**:

```yml
collections:
  authors:
    output: true

defaults:
  - scope:
      path: ""
      type: "authors"
    values:
      layout: "author"
  - scope:
      path: ""
      type: "posts"
    values:
      layout: "post"
  - scope:
      path: ""
    values:
      layout: "default"
```

Now you can remove layout from the front matter of all pages and posts. Note that any time you update **`_config.yml`** you’ll need to **restart Jekyll** for the changes to take effect.

###### LIST AUTHOR'S POSTS

Let’s list the posts an author has published on their page. To do this you need to match the author **`short_name`** to the post **`author`**. You use this to filter the posts by author.

Iterate over this filtered list in **`_layouts/author.html`** to output the author’s posts:

```liquid
---
layout: default
---
<h1>{{ page.name }}</h1>
<h2>{{ page.position }}</h2>

{{ content }}

<h2>Posts</h2>
<ul>
  {% assign filtered_posts = site.posts | where: 'author', page.short_name %}
  {% for post in filtered_posts %}
    <li><a href="}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
```

###### LINK TO AUTHOR'S PAGE

The posts have a reference to the author so let’s link it to the author’s page. You can do this using a similar filtering technique in **`_layouts/post.html`**:

```liquid
---
layout: default
---
<h1>{{ page.title }}</h1>

<p>
  {{ page.date | date_to_string }}
  {% assign author = site.authors | where: 'short_name', page.author | first %}
  {% if author %}
    - <a href="{% raw %}{{ author.url }}">{{ author.name }}</a>
  {% endif %}
</p>

{{ content }}
```

Open up http://localhost:4000 and have a look at the staff page and the author links on posts to check everything is linked together correctly.

##### DEPLOYMENT

In this final step we’ll get the site ready for production.

###### GEMFILE

It’s good practice to have a [Gemfile](https://jekyllrb.com/docs/ruby-101/#gemfile) for your site. This ensures the version of Jekyll and other gems remains consistent across different environments.

Create a **`Gemfile`** in the root. The file should be called ‘Gemfile’ and should not have any extension. You can create a Gemfile with Bundler and then add the **`jekyll`** gem:

```bash
bundle init
bundle add jekyll
```

Your file should look something like:

```bash
# frozen_string_literal: true
source "https://rubygems.org"

gem "jekyll"
```

Bundler installs the gems and creates a **`Gemfile.lock`** which locks the current gem versions for a future **`bundle install`**. If you ever want to update your gem versions you can run **`bundle update`**.

When using a **`Gemfile`**, you’ll run commands like **`jekyll serve`** with **`bundle exec`** prefixed. So the full command is:

```bash
bundle exec jekyll serve
```

This restricts your Ruby environment to only use gems set in your **`Gemfile`**.

###### PLUGINS

Jekyll plugins allow you to create custom generated content specific to your site. There’s many [plugins](https://jekyllrb.com/docs/plugins/) available or you can even write your own.

There are three official plugins which are useful on almost any Jekyll site:

- [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap) - Creates a sitemap file to help search engines index content.
- [jekyll-feed](https://github.com/jekyll/jekyll-feed) - Creates an RSS feed for your posts.
- [jekyll-seo-tag](https://github.com/jekyll/jekyll-seo-tag) - Adds meta tags to help with SEO.

To use these first you need to add them to your **`Gemfile`**. If you put them in a **`jekyll_plugins`** group they’ll automatically be required into Jekyll:

```bash
source 'https://rubygems.org'

gem 'jekyll'

group :jekyll_plugins do
  gem 'jekyll-sitemap'
  gem 'jekyll-feed'
  gem 'jekyll-seo-tag'
end
```

Then add these lines to your **`_config.yml`**:

```yml
plugins:
  - jekyll-feed
  - jekyll-sitemap
  - jekyll-seo-tag
```

Now install them by running a **`bundle update`**.

**`jekyll-sitemap`** doesn’t need any setup, it will create your sitemap on build.

For **`jekyll-feed`** and **`jekyll-seo-tag`** you need to add tags to **`_layouts/default.html`**:

```html
<!doctype html>
<html>
  <head>
    <meta charset="utf-8">
    <title>{% raw %}{{ page.title }}{% endraw %}</title>
    <link rel="stylesheet" href="/assets/css/styles.css">
    {% raw %}{% feed_meta %}{% endraw %}
    {% raw %}{% seo %}{% endraw %}
  </head>
  <body>
    {% raw %}{% include navigation.html %}{% endraw %}
    {% raw %}{{ content }}{% endraw %}
  </body>
</html>
```

Restart your Jekyll server and check these tags are added to the **`<head>`**.

###### ENVIRONMENTS

Sometimes you might want to output something in production but not in development. Analytics scripts are the most common example of this.

To do this you can use [environments](https://jekyllrb.com/docs/configuration/environments/). You can set the environment by using the **`JEKYLL_ENV`** environment variable when running a command. For example:

```bash
JEKYLL_ENV=production bundle exec jekyll build
```

By default **`JEKYLL_ENV`** is development. The **`JEKYLL_ENV`** is available to you in liquid using **`jekyll.environment`**. So to only output the analytics script on production you would do the following:

```liquid
{% if jekyll.environment == "production" %}
  <script src="my-analytics-script.js"></script>
{% endif %}
```

###### DEPLOYMENT

The final step is to get the site onto a production server. The most basic way to do this is to run a production build:

```bash
JEKYLL_ENV=production bundle exec jekyll build
```

And copy the contents of **`_site`** to your server.

A better way is to automate this process using a [CI](https://jekyllrb.com/docs/deployment/automated/) or [3rd party](https://jekyllrb.com/docs/deployment/third-party/).

### Wrap up

That brings us to the end of this step-by-step tutorial and the beginning of your Jekyll journey!

## Ruby and Gems

### Gemfile

A **Gemfile** is a list of gems used by your site. Every Jekyll site has one in the main folder.

Example:

```
source "https://rubygems.org"

gem "jekyll"

group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end
```

### Bundler

**Bundler** is a gem that installs all gems in your Gemfile.

While you don’t have to use Gemfile and bundler, it is highly recommended as it ensures you’re running the same version of Jekyll and its plugins across different environments.

Install Bundler using **`gem install bundler`**. You only need to install it once, not every time you create a new Jekyll project.

To install gems in your Gemfile using Bundler, run the following in the directory that has the Gemfile:

```bash
bundle install
bundle exec jekyll serve
```

More info about using Bundler with Jekyll [at this page](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/).

## Support & documentation

- Read the [Jekyll Documentation](https://jekyllrb.com/docs/).
- If you have a question about using Jekyll, start a discussion on the [Jekyll Forum](https://talk.jekyllrb.com/) or [StackOverflow](https://stackoverflow.com/questions/tagged/jekyll).
- Videos from [Jekyllconf](https://jekyllrb.com/jekyllconf/).

## Convert WordPress to Jekyll

- Export WP posts to `.xml` through the export functionality.

- Install Jekyll WordPress importer:

  `sudo gem install jekyll-import`
    
  `sudo gem install hpricot`
    
- Install open URI redirections:

  `gem install open_uri_redirections`

- Run Jekyll WordPress importer:

  `ruby -rrubygems -e 'require "jekyll-import"; JekyllImport::Importers::WordpressDotCom.run({ "source" => "wordpress.xml" })'`

# Jekyll snippets

## Access static files

According to the official [Jekyll documentation](https://jekyllrb.com/docs/static-files/), “a static file is a file that does not contain any YAML front matter. These include images, PDFs, and other un-rendered content.”

The useful bit: **every one of these static files becomes accessible to Jekyll when looping** through `site.static_files`. There aren’t many reasons why you’d want to do this, but building “plugin-free” image galleries is one of them.

### Example accessing static files

Fictitious image gallery in the filesystem:

```
├── assets/
│   └── images/
│       └── gallery-1/
│           ├── foo.jpg
│           ├── bar.gif
│           └── yaz.png
```

Using Liquid, you’d start by looping through `site.static_files` and then narrow down the files based on their paths. In this case we only want to show those images that live together in `assets/images/gallery-1`.

```liquid
{% for image in site.static_files %}{% endraw %}
  {% if image.path contains 'assets/images/gallery-1' %}
    <img src="{% raw %}{{ image.path }}{% endraw %}" alt="">
  {% endif %}
{% endfor %}
```

Which will generate into the following HTML:

```html
<img src="assets/images/gallery-1/bar.gif" alt="">
<img src="assets/images/gallery-1/foo.jpg" alt="">
<img src="assets/images/gallery-1/yaz.png" alt="">
```

Each static file contains metadata accessible via Liquid with the following variables:

|Variable|Description|
|--- |--- |
|`file.path`|The relative path to the file, e.g., `/assets/img/image.jpg`|
|`file.modified_time`|The time the file was last modified, e.g., `2016-04-01 16:35:26 +0200`|
|`file.name`|The string name of the file e.g., `image.jpg` for `image.jpg`|
|`file.basename`|The string basename of the file e.g., `image` for `image.jpg`|
|`file.extname`|The extension name for the file, e.g., `.jpg` for `image.jpg`|

> **`NOTE`**
> 
> **Filename consistency is paramount**
> 
> Using this method to build a gallery of thumbnail images is fragile. The `image` objects inside of these loops are not validated by Jekyll at all. If you call in paths that don’t exist it will silently fail and leave you with missing images on the page.

---

#Jekyll