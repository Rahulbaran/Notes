# [At-rules](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule)

- These are the **CSS Statements** which instruct **CSS** how to behave.

- They starts with `@` sign followed by an identifier & includes everything upto the next **semicolon** or the next **CSS block** whichever comes first.

## Regular At-rules

- It uses semicolon.

```css
/*--- General Structure ---*/
@identifier (RULE);

/*--- example ---*/
@charset "utf-8";
```

- There are several regular at-rules which are:-

  - `@charset`- To define character set used by stylesheet.
  - `@import`- Tells CSS engine to include an external stylesheet.
  - `@namespace` - Tells CSS engine that all its content must be considered prefixed with an XML namespace.

## Nested At-rules

- It uses CSS block(`{}`).

```css
/* Syntax */
@identifier (RULE) {
    -----
}

/* Example */
@property --name {
  syntax: "<color>";
  initial-value: red;
  inherits: false
}
```

- These can be used as a statement of a stylesheet as well as inside of **Conditional group rules** (`@media, @supports, @document`).

  - `@media`
  - `@supports`
  - `@page`
  - `@font-face`
  - `@keyframes`
  - `@counter-style`
  - `@font-feature-values`
  - `@property`(Experimental)
  - `@layer`
  - `@color-profile`(Experimental)
  - `@document` (Deprecated)
  - `@viewport` (Deprecated)

#### @media

- Mentioned values in its block are applied if a device meets certain criteria defined.
- **Example**

```css
@media (prefers-reduced-motion) {
  html {
    scroll-behavior: auto;
  }
}
@media all and (min-width: 992px) {
  .container {
    grid-template-columns: repeat(2, 1fr);
  }
}
```

#### @supports

- Rules are applied to mentioned contents if the browser meets certain criteria mentioned as condition.
- **Example**

```css
@supports (text-align: start) {
  h1 {
    text-align: start;
  }
}
@supports not (text-align: start) {
  h1 {
    text-align: left;
  }
}
```

### @property

- It provides a way to specify a **type** for custom CSS properties.
- We can give the browser the information it needs to transition and animate custom properties.
- **Example**

```css
@property --stop {
  inherits: false;
  initial-value: 30%;
  syntax: "<color>";
}
```

- Various available **types** are following:-
  - `length`
  - `number`
  - `color`
  - `percentage`
  - `integer`
  - `length-percentage`
  - `image`
  - `url`
  - `angle`
  - `time`
  - `resolution`
  - `transform-list`
  - `transform-function`
  - `custom-indent`

### @layer

- When a browser composites styles, there are 3 primary origins:-
  - **Author origin** - Stylesheets add to website.
  - **User origin** - Styles that browsers may allow providing as preferences such as default font, font size & colors.
  - **User-Agent origin** - The default styles applied by the browser.
- Cascade sorting order by priority is as follows:-
  - Origins & importance
  - Context(inside a shadow DOM)
  - Style Attribute
  - Specificity
  - Order of Appearance
- When writting CSS, We work in **Author origin** & deal with only **Specificity** & **Order of Appearance**.
- Cascade layers aim to place control of both in the hands of author Since it is given higher precendence than **Specificity** & **Order of Appearance**.
- Cascade layers are about structuring CSS code & controlling the CSS Cascade.
- We use `@layer` to creating cascade layers and order of these layers matter.

#### Defining Cascade Layers

1. Using `@layer` with a block for layer styles

```css
@layer base {
  <element > {
  }
}
```

2. Using `@import` with `layer()` function

```css
@import url(header.css) layer(navigation);
```

- We can also define layer order in one place at the top & then can use them later.
- Later whatever styles we append in the same layer on multiple places, it will be appended to it.

```css
@layer base, navigation, application;
@import url(footer.css) layer(footer);

@layer base {
  .container {
    ...;
  }
}

@layer footer {
  body {
    ...;
  }
}

/* All the styles will be appended to @layer base  */
@layer base {
  h1,
  h2,
  h3,
  h4 {
    ...;
  }
}
```

#### Nesting Cascade Layers

- We can also nest `@layer` rules and to add onto nested rules later, we reference parent & nested rules together usnig dot notation.

```css
@layer native {
  @layer reset, base, components;
}

@layer native.base {
  ...;
}
```

-

> [Article on](https://www.bram.us/2021/09/15/the-future-of-css-cascade-layers-css-at-layer/) `@layer`
