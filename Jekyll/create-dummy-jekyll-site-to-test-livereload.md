# Check on a new jekyll dummy website

Real-life scenario: I want to check if the `livereload` option works. Create a new dummy Jekyll site and use it to test.

```bash
$ jekyll new foo
$ cd foo
$ bundle exec jekyll serve --open-url --livereload
```

Now edit index.markdown to see if page reloads
