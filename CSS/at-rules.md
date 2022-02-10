# [At-rules](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule)

- These are the **CSS Statements** which instruct **CSS** how to behave.

- They starts with `@` sign followed by an identifier & includes everything upto the next **semicolon** or the next **CSS block** whichever comes first.

### Regular At-rules (use semicolon)

```css
/*--- General Structure ---*/
@identifier (RULE);

/*--- example ---*/
@charset "utf-8";
```

- There are several regular at-rules which are:-

  - `@charset`- To define character set used by stylesheet
  - `@import`- Tells CSS engine to include an external stylesheet
  - `@namespace` - Tells CSS engine that all its content must be considered prefixed with an XML namespace

### Nested At-rules (use CSS block)

```css
@identifier (RULE) {
    -----
}
```

- These can be used as a statement of a stylesheet as well as inside of **Conditional group rules** (`@media, @supports, @document`).

  - `@media` - It will apply its content if a device meets certain criteria defined using a media query.

  - `@supports` - It will apply its content if the browser meets certain criteria mentioned as condition.

  - `@document` (Deprecated)

  - `@page`

  - `@font-face`

  - `@keyframes`

  - `@viewport` (Deprecated)

  - `@counter-style`

  - `@font-feature-values`

  - `@property`

  - `@color-profile`
