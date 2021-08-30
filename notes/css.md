# Cascading Style Sheets (CSS)

__CSS__ is the @[language][programming-language] used to apply styles to @[HTML][]
documents. CSS is not a general purpose language, and cannot be used for anything
else but applying styles.

The general structure of a css file is a collection of rules of the following form:

```css
selector {
  attribute: value;
}
```

The @[selector][css-selector] is used to identify which elements in the document
should be affected by the rule, then the listed attributes and values are applied
to those elements.

Though it seems simple, there are a bunch of strange rules with how the selectors
and attributes interact and overrule each other (i.e. how they *cascade*).

Since the language is pretty limited in what can be done and how the code can be
structured, there are a number of @[methodologies][css-methodologies] by which
people structure their CSS selectors and rules so they are easy to understand.

To make the actual experience of writing CSS easier or more enjoyable, preprocessors
such as @[Sass][sass-css] or @[PostCSS][] have been created.

Some useful resources:
*   [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS)
*   [CSS-Tricks](https://css-tricks.com/)
