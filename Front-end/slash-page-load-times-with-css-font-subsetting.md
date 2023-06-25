# Slash page load times with CSS font subsetting

The wide availability of web fonts has enabled sites to become typographical wonderlands, at the cost of increased page size and longer load times. Performance-focused developers already optimise their images and CSS; it makes sense that we should also optimise web fonts.

The good news is that doing is fairly easy: by creating your own custom font or supplying your web font hosting service with a simple variable value, you can load only the glyphs that you need for the text you have on the page, rather than the entire range of characters, numbers and symbols in the font, reducing page load times.

Font subsetting can be very effective, provided you keep two conditions in mind:

- In order to use the most effective versions of this technique – loading a limited range of characters from the font – you should be certain that text rendered in that font will not change substantially in the future, as glyphs that arenʼt explicitly loaded wonʼt display correctly. 
- If you are self-hosting the web font, you should ensure that non-WOFF fonts are gzipped first, which will save an average of 40 ~ 70% on file size, before turning your attention to gaining advantages from subsetting.

## Subsetting Self-Hosted Web Fonts

You can also subset fonts from your own server bycreating a custom font that contains only the glyphs you want. Itʼs often (and understandably) assumed that the CSS unicode-range property subsets fonts. This is only partially true: under Unicode-range the entire font is still loaded, but only the characters in a set range are actually used. As such, itʼs not a webfont optimization technique of the kind weʼre discussing here, and doesnʼt save on download time.

The easiest way to do that currently is by using the Expert option in the Font Squirrel webfont generator service: Obviously, you must be assured that you can manipulate the font in this way: read the license agreement first. In this case, Iʼve decided that I only want to use capital letters from the Lobster font. Extracting these into a webfont yields a much smaller file than the original: I can assure that uppercase letters will only be typeset in Lobster on my site by stating so in my CSS:

```css
@font-face { font-family: Lobster; src: url("Lobster/lobster-caps.woff");
h1 { font-family: Lobster; text-transform: uppercase; }
```

If youʼre only using a few characters from a font, it may be worthwhile base-64 encoding the result, saving yourself a HTTP request; rendering the unique glyphs in SVG would also be an option.

## Conclusion

Subsetting your fonts can be an extremely powerful and useful tool, but needs to be carefully considered and planned for. The demands of designers, content providers and translators should all be considered when choosing what text range to use in a font subset.

---

#CSS #FrontEnd