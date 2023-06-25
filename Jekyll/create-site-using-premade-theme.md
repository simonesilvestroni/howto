# Create a Jekyll site using a pre-made theme

Jekyll has an extensive theme system that allows you to leverage community-maintained templates and styles to customize your site’s presentation. Jekyll themes specify plugins and package up assets, layouts, includes, and stylesheets in a way that can be overridden by your site’s content.

You can find and preview themes on different galleries:

-   [GitHub.com #jekyll-theme repos](https://github.com/topics/jekyll-theme)
-   [jamstackthemes.dev](https://jamstackthemes.dev/ssg/jekyll/)
-   [jekyllthemes.org](http://jekyllthemes.org/)
-   [jekyllthemes.io](https://jekyllthemes.io/)
-   [jekyll-themes.com](https://jekyll-themes.com/)

See also: [resources](https://jekyllrb.com/resources/).

## Understanding gem-based themes

When you [create a new Jekyll site](https://jekyllrb.com/docs/) (by running the `jekyll new <PATH>` command), Jekyll installs a site that uses a gem-based theme called [Minima](https://github.com/jekyll/minima).

With gem-based themes, some of the site’s directories (such as the `assets`, `_data`, `_layouts`, `_includes`, and `_sass` directories) are stored in the theme’s gem, hidden from your immediate view. Yet all of the necessary directories will be read and processed during Jekyll’s build process.

In the case of Minima, you see only the following files in your Jekyll site directory:

```
. 
├── Gemfile 
├── Gemfile.lock 
├── _config.yml 
├── 📁 _posts 
│    └── 2016-12-04-welcome-to-jekyll.markdown 
├── about.markdown 
└── index.markdown
```

The `Gemfile` and `Gemfile.lock` files are used by Bundler to keep track of the required gems and gem versions you need to build your Jekyll site.

Gem-based themes make it easier for theme developers to make updates available to anyone who has the theme gem. When there’s an update, theme developers push the update to RubyGems.

If you have the theme gem, you can (if you desire) run `bundle update` to update all gems in your project. Or you can run `bundle update <THEME>`, replacing `<THEME>` with the theme name, such as `minima`, to just update the theme gem. Any new files or updates the theme developer has made (such as to stylesheets or includes) will be pulled into your project automatically.

The goal of gem-based themes is to allow you to get all the benefits of a robust, continually updated theme without having all the theme’s files getting in your way and over-complicating what might be your primary focus: creating content.

## Overriding theme defaults

Jekyll themes set default data, layouts, includes, and stylesheets. However, you can override any of the theme defaults with your own site content.

To replace layouts or includes in your theme, make a copy in your `_layouts` or `_includes` directory of the specific file you wish to modify, or create the file from scratch giving it the same name as the file you wish to override.

For example, if your selected theme has a `page` layout, you can override the theme’s layout by creating your own `page` layout in the `_layouts` directory (that is, `_layouts/page.html`).

To locate a theme’s files on your computer:

1.  Run `bundle info --path` followed by the name of the theme’s gem, e.g., `bundle info --path minima` for Jekyll’s default theme.
    
    This returns the location of the gem-based theme files. For example, the Minima theme’s files might be located in `/usr/local/lib/ruby/gems/2.6.0/gems/minima-2.5.1` on macOS.
    
2.  Open the theme’s directory in Finder:

```bash
# On MacOS
open $(bundle info --path minima)
```

A Finder or Explorer window opens showing the theme’s files and directories. The Minima theme gem contains these files:

```
.
├── LICENSE.txt
├── README.md
├── 📁 _includes
│   ├── disqus_comments.html
│   ├── footer.html
│   ├── google-analytics.html
│   ├── head.html
│   ├── header.html
│   ├── icon-github.html
│   ├── icon-github.svg
│   ├── icon-twitter.html
│   └── icon-twitter.svg
├── 📁 _layouts
│   ├── default.html
│   ├── home.html
│   ├── page.html
│   └── post.html
├── 📁 _sass
│   ├── minima
│   │   ├── _base.scss
│   │   ├── _layout.scss
│   │   └── _syntax-highlighting.scss
│   └── minima.scss
└── 📁 assets
    └── main.scss
```

With a clear understanding of the theme’s files, you can now override any theme file by creating a similarly named file in your Jekyll site directory.

Let’s say, for a second example, you want to override Minima’s footer. In your Jekyll site, create an `_includes` folder and add a file in it called `footer.html`. Jekyll will now use your site’s `footer.html` file instead of the `footer.html` file from the Minima theme gem.

To modify any stylesheet you must take the extra step of also copying the main sass file (`_sass/minima.scss` in the Minima theme) into the `_sass` directory in your site’s source.

Jekyll will look first to your site’s content before looking to the theme’s defaults for any requested file in the following folders:

- `📁 _data`
- `📁 _layouts`
- `📁 _includes`
- `📁 _sass`
- `📁 assets`

Note that making copies of theme files will prevent you from receiving any theme updates on those files. An alternative, to continue getting theme updates on all stylesheets, is to use higher specificity CSS selectors in your own additional, originally named CSS files.

## Converting gem-based themes to regular themes

Suppose you want to get rid of the gem-based theme and convert it to a regular theme, where all files are present in your Jekyll site directory, with nothing stored in the theme gem.

To do this, copy the files from the theme gem’s directory into your Jekyll site directory. (For example, copy them to `/myblog` if you created your Jekyll site at `/myblog`. See the previous section for details.)

Then you must tell Jekyll about the plugins that were referenced by the theme. You can find these plugins in the theme’s gemspec file as runtime dependencies. If you were converting the Minima theme, for example, you might see:

```ruby
spec.add_runtime_dependency "jekyll-feed", "~> 0.12"
spec.add_runtime_dependency "jekyll-seo-tag", "~> 2.6"
```

You should include these references in the `Gemfile` in one of two ways.

You could list them individually in both `Gemfile` and `_config.yml`.

```ruby
# ./Gemfile

gem "jekyll-feed", "~> 0.12"
gem "jekyll-seo-tag", "~> 2.6"
```

```ruby
# ./_config.yml

plugins:
  - jekyll-feed
  - jekyll-seo-tag
```

Or you could list them explicitly as Jekyll plugins in your Gemfile, and not update `_config.yml`, like this:

```ruby
# ./Gemfile

group :jekyll_plugins do
  gem "jekyll-feed", "~> 0.12"
  gem "jekyll-seo-tag", "~> 2.6"
end
```

Either way, don’t forget to `bundle update`.

If you’re publishing on GitHub Pages you should update only your `_config.yml` as GitHub Pages doesn’t load plugins via Bundler.

Finally, remove references to the theme gem in `Gemfile` and configuration. For example, to remove `minima`:

-  Open `Gemfile` and remove `gem "minima", "~> 2.5"`.
-  Open `_config.yml` and remove `theme: minima`.

Now `bundle update` will no longer get updates for the theme gem.

## Installing a gem-based theme

The `jekyll new <PATH>` command isn’t the only way to create a new Jekyll site with a gem-based theme. You can also find gem-based themes online and incorporate them into your Jekyll project.

For example, search for [jekyll theme on RubyGems](https://rubygems.org/search?utf8=%E2%9C%93&query=jekyll-theme) to find other gem-based themes. (Note that not all themes are using `jekyll-theme` as a convention in the theme name.)

To install a gem-based theme:

1 - Add the theme gem to your site’s `Gemfile`:

```ruby
# ./Gemfile

# This is an example, declare the theme gem you want to use here
gem "jekyll-theme-minimal"
```

Or if you’ve started with the `jekyll new` command, replace `gem "minima", "~> 2.0"` with the gem you want, e.g:

```ruby
# ./Gemfile

- gem "minima", "~> 2.5"
+ gem "jekyll-theme-minimal"
```

2 - Install the theme:

```bash
bundle install
```

3 - Add the following to your site’s `_config.yml` to activate the theme:

```ruby
theme: jekyll-theme-minimal
```

4 - Build your site:

```bash
bundle exec jekyll serve
```

---

### Notes

You can have multiple themes listed in your site’s Gemfile, but only one theme can be selected in your site’s `_config.yml`.

If you’re publishing your Jekyll site on [GitHub Pages](https://pages.github.com/), note that GitHub Pages supports only [some gem-based themes](https://pages.github.com/themes/). GitHub Pages also supports [using any theme hosted on GitHub](https://help.github.com/articles/adding-a-jekyll-theme-to-your-github-pages-site/#adding-a-jekyll-theme-in-your-sites-_configyml-file) using the `remote_theme` configuration as if it were a gem-based theme.

More info: [https://jekyllrb.com/docs/themes/](https://jekyllrb.com/docs/themes/)

---

## EXAMPLE: Minimal Mistakes (theme)

Minimal Mistakes is a flexible two-column Jekyll theme, perfect for building personal sites, blogs, and portfolios. As the name implies, styling is purposely minimalistic to be enhanced and customized by you.

**Note:** The theme uses the [jekyll-include-cache](https://github.com/benbalter/jekyll-include-cache) plugin which will need to be installed in your `Gemfile` and must be retained in the `plugins` array of `_config.yml`. Otherwise you'll encounter `Unknown tag 'include_cached'` errors at build.

### GitHub repo

[https://github.com/mmistakes/minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)

### Notable features

- Bundled as a "theme gem" for easier installation/upgrading.
- Compatible with GitHub Pages.
- Support for Jekyll's built-in Sass/SCSS preprocessor.
- Nine different skins (color variations).
- Several responsive layout options (single, archive index, search, splash, and paginated home page).
- Optimized for search engines with support for [Twitter Cards](https://dev.twitter.com/cards/overview) and [Open Graph](http://ogp.me/) data.
- Optional [header images](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#headers), [custom sidebars](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#sidebars), [table of contents](https://mmistakes.github.io/minimal-mistakes/docs/helpers/#table-of-contents), [galleries](https://mmistakes.github.io/minimal-mistakes/docs/helpers/#gallery), related posts, [breadcrumb links](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#breadcrumb-navigation-beta), [navigation lists](https://mmistakes.github.io/minimal-mistakes/docs/helpers/#navigation-list), and more.
- Commenting support (powered by [Disqus](https://disqus.com/), [Facebook](https://developers.facebook.com/docs/plugins/comments), Google+, [Discourse](https://www.discourse.org/), static-based via [Staticman](https://staticman.net/), [utterances](https://utteranc.es/), and [giscus](https://giscus.app/)).
- [Google Analytics](https://www.google.com/analytics/) support.
- UI localized text in English (default), Arabic (عربي), Brazilian Portuguese (Português brasileiro), Catalan, Chinese, Danish, Dutch, Finnish, French (Français), German (Deutsch), Greek, Hebrew, Hindi (हिंदी), Hungarian, Indonesian, Irish (Gaeilge), Italian (Italiano), Japanese, Korean, Malayalam, Myanmar (Burmese), Nepali (Nepalese), Norwegian (Norsk), Persian (فارسی), Polish, Punjabi (ਪੰਜਾਬੀ), Romanian, Russian, Slovak, Spanish (Español), Swedish, Thai, Turkish (Türkçe), and Vietnamese.

### Skins (color variations)

This theme comes in nine different skins (in addition to the default one).

### Demo pages

<table>
<thead>
<tr>
<th>Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><a href="https://mmistakes.github.io/minimal-mistakes/layout-header-image-text-readability/" rel="nofollow">Post with Header Image</a></td>
<td>A post with a large header image.</td>
</tr>
<tr>
<td><a href="https://mmistakes.github.io/minimal-mistakes/markup/markup-html-tags-and-formatting/" rel="nofollow">HTML Tags and Formatting Post</a></td>
<td>A variety of common markup showing how the theme styles them.</td>
</tr>
<tr>
<td><a href="https://mmistakes.github.io/minimal-mistakes/markup-syntax-highlighting/" rel="nofollow">Syntax Highlighting Post</a></td>
<td>Post displaying highlighted code.</td>
</tr>
<tr>
<td><a href="https://mmistakes.github.io/minimal-mistakes/post%20formats/post-gallery/" rel="nofollow">Post with a Gallery</a></td>
<td>A post showing several images wrapped in <code>&lt;figure&gt;</code> elements.</td>
</tr>
<tr>
<td><a href="https://mmistakes.github.io/minimal-mistakes/recipes/chocolate-chip-cookies/" rel="nofollow">Sample Collection Page</a></td>
<td>Single page from a collection.</td>
</tr>
<tr>
<td><a href="https://mmistakes.github.io/minimal-mistakes/categories/" rel="nofollow">Categories Archive</a></td>
<td>Posts grouped by category.</td>
</tr>
<tr>
<td><a href="https://mmistakes.github.io/minimal-mistakes/tags/" rel="nofollow">Tags Archive</a></td>
<td>Posts grouped by tag.</td>
</tr>
</tbody>
</table>

Additional sample posts are available under [posts archive](https://mmistakes.github.io/minimal-mistakes/year-archive/) on the demo site. Source files for these (and the entire demo site) can be found in [`/docs`](https://github.com/mmistakes/minimal-mistakes/blob/master/docs).

### Installation

There are three ways to install: 

1. as a [gem-based theme](https://jekyllrb.com/docs/themes/#understanding-gem-based-themes),
2. as a [remote theme](https://blog.github.com/2017-11-29-use-any-theme-with-github-pages/) (GitHub Pages compatible),
3. forking/directly copying all of the theme files into your project.

#### Gem-based method

With Gem-based themes, directories such as the `assets`, `_layouts`, `_includes`, and `_sass` are stored in the theme’s gem, hidden from your immediate view. Yet all of the necessary directories will be read and processed during Jekyll’s build process.

This allows for easier installation and updating as you don't have to manage any of the theme files. To install:

1. Add the following to your `Gemfile`:
   
```ruby
gem "minimal-mistakes-jekyll"
```

2. Fetch and update bundled gems by running the following [Bundler](http://bundler.io/) command:
   
```bash
bundle
```

3. Set the `theme` in your project's Jekyll `_config.yml` file:
   
```ruby
theme: minimal-mistakes-jekyll
```

To update the theme run `bundle update`.

#### Remote theme method

Remote themes are similar to Gem-based themes, but do not require `Gemfile` changes or whitelisting making them ideal for sites hosted with GitHub Pages.

To install:

1. Create/replace the contents of your `Gemfile` with the following:
   
```ruby
source "https://rubygems.org"
    
gem "github-pages", group: :jekyll\_plugins
gem "jekyll-include-cache", group: :jekyll\_plugins`
```

2. Add `jekyll-include-cache` to the `plugins` array of your `_config.yml`.
   
3. Fetch and update bundled gems by running the following [Bundler](http://bundler.io/) command:
   
```bash
bundle
```

4. Add `remote_theme: "mmistakes/minimal-mistakes@4.24.0"` to your `_config.yml` file. Remove any other `theme:` or `remote_theme:` entry.
   

**Looking for an example?** Use the [Minimal Mistakes remote theme starter](https://github.com/mmistakes/mm-github-pages-starter/generate) for the quickest method of getting a GitHub Pages hosted site up and running. Generate a new repository from the starter, replace sample content with your own, and configure as needed.

### Usage

For detailed instructions on how to configure, customize, add/migrate content, and more read the [theme's documentation](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/).

---

## EXAMPLE: Beautiful Jekyll (theme)

- **Repo**: [https://github.com/daattali/beautiful-jekyll](https://github.com/daattali/beautiful-jekyll).
- **Demo**: [https://beautifuljekyll.com/](https://beautifuljekyll.com/)

---

#Jekyll