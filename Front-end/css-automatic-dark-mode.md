# Automatic dark mode in CSS

Setting dark mode based on the operating system's settings is the easiest way to enable dark mode. If the user is using dark mode on their phone, tablet or computer, we can then show our website in dark mode by using the following CSS:

```css
/* Light mode CSS */
body {
  background: white;
}
@media (prefers-color-scheme: dark) {
  body {
    background: black;
  }
}
```

## Resources

- [Automatic dark mode with CSS variables, by Make Babb](https://mikebabb.com/blog/automatic-dark-mode-with-css-variables/)
- [The benefits of using dark mode, on Sustainable Dev](https://the-sustainable.dev/the-benefits-of-using-dark-mode/)