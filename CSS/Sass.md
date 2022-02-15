# [Sass(Syntactically Awesome Stylesheet)](https://sass-lang.com/documentation)

- A CSS Preprocessor (a stylesheet language) which is compiled to CSS.

- A Preprocessor is a program which takes input & produces output which is used as input by another program.

- It helps keep large stylesheets well-organized & makes it easy to share design within & across projects.

- It supports two different syntaxes:-

  1. **SCSS(Sassy CSS)** - It uses file extension `.scss`. It is a superset of CSS which means **all valid css is valid scss as well**.

  ```scss
  @mixin flex($just, $align) {
    display: flex;
    justify-content: $just;
    align-items: $align;
  }
  ```

  2. **The Indented Syntax** - It is based on Indentation rather than block and uses file extension `.sass`. It is sometimes called **Sass** because of extension.

  ```sass
  @mixin flex($just, $align)
   display: flex;
   justify-content: $just;
   align-items: $align;
  ```

- **CSS** automatically recovers from **most invalid syntaxes** raised in the stylesheet whereas **Sass** fails parsing & raises error with specifying the location of invalid syntax & cause of error.

- Here, We will mainly focus on **SCSS**.

## Syntax

### Statements

- A series of _statements_ is used to build up a **Sass** stylesheet which is evaluated to get the resulting **CSS**.

- There are following types of _statements_:-

  1. Universal Statements - These statements can be used anywhere in a **Sass** stylesheet:

     - Variable Declarations (for eg:- $var:value)
     - Flow control at-rules (like `@if` & `@each`)

  2. CSS Statements - These statements can be used anywhere except within a `@function`:

     - Style rules (like `h1 { ... }`)
     - CSS at-rules (like `@supports`, `@page`, `@media`)
     - `@include` for Mixin use
     - `@at-root` rule

  3. Top-Level Statements - These statements can only be used at top level of a stylesheet/nested within a **CSS** statement at top level:

     - `@use` for loading Modules
     - `@import` for imports
     - `@mixin` for defining Mixin
     - `@function` for defining funtions

  4. Other Statements

     - Property declarations like `pointer:none;` only within style rules & some css at-rules.

     - `@extend` rule only within style rules.

### Expression

- It is anything which goes on the right hand side of a property/variable declaration.

- Each expression produces a **value**.

- Any valid **CSS** property value is also a **Sass** _expression_.

### Comments

- Single line comments start with **//**, They are also called **silent comments** because they don't produce any **CSS**.

- Multi-line comments start with **/\*** & end with **\*/**. They are also called **loud comments**.

- If a Multi-line comment starts with **/\*!** then it will always be included in the css output.

## Style Rules

### Nesting

- **Sass** allows writing of one style rule inside another rather than repeating the same selectors over & over.

- Nesting of selectors should be **shallow** to avoid complexity in visualizing and save bandwidth required to parse it to **CSS**.

```css
/*-------------- SASS -------------*/
section {
  background-color: red;
  p {
    color: blue;
  }
}

/*------------- CSS --------------*/
section {
  background-color: red;
}
section p {
  color: blue;
}
```

- We can handle Selector lists of complex selectors through by nesting them.

```css
/*--------------- SASS ---------------*/
.header,
.footer {
  span,
  h3 {
    font-family: "Roboto", sans-serif;
  }
}

/*-------------- CSS ---------------*/
.header span,
.header h3,
.footer span,
.footer h3 {
  font-family: "Roboto", sans-serif;
}
```

- We can also nest selectors which use **combinators**.

```css
/*------------ SASS -------------*/
.card {
  > div {
    margin-top: 1rem;
  }
}
.card + {
  .card {
    margin: 0.5rem 0;
  }
}
h1 {
  ~ {
    p {
      font-size: 1.1rem;
    }
  }
}

/*------------- CSS --------------*/
.card div {
  margin-top: 1rem;
}
.card + .card {
  margin: 0.5rem 0;
}
h1 ~ p {
  font-size: 1.1rem;
}
```

- There are various **CSS** properties which start with same prefix & **Sass** makes it easier & less redundant by allowing these property declarations to be nested.

```css
/*-------------- SASS ---------------*/
.container {
  font: {
    size: 1rem;
    weight: 400;
    family: "Abeezee", sans-serif;
  }

  &:nth-of-type(2n + 1) {
    background-color: hsl(240deg 100% 90%);
  }
}

/*-------------- CSS ----------------*/
.container {
  font-size: 1rem;
  font-weight: 400;
  font-family: "Abeezee", sans-serif;
}

.container:nth-of-type(2n + 1) {
  background-color: hsl(240deg 100% 90%);
}
```

### Interpolation

- It is used to inject **expressions** like variables, functions calls into a selector.

- It always returns an **unquoted string** in **SassScript** which is quite useful for generating dynamic names.

- It is very useful while writing **mixins** because it allows creating selectors from the parameters passed in.

- It uses `#{}` syntax for injection.

```css
/*------------ SCSS -------------*/
@mixin define-margin($size, $value) {
  .m-#{$size} {
    margin: #{$value};
  }
}
@include define-margin(4, 4px);
@include define-margin(6, 6px);
@include define-margin(8, 8px);

/*----------- CSS -----------*/
.m-4 {
  margin: 4px;
}
.m-6 {
  margin: 6px;
}
.m-8 {
  margin: 8px;
}
```

- **Sass** only parses selectors after _interpolation_ is resolved. That's why we can generate any part of selector safely using _interpolation_ without worrying that it will not parse.

- Since _interpolation_ returns unquoted string that's it is a bad idea to use it with numbers since it can't be used for any math operation.

- For numbers we can use **unit arithmetic** instead of _interpolation_. For example, instead of writing `#{$width}px`, write `$width * 1px` or better yet, declare the `$width` variable in terms of `px` to begin with. That way if `$width` already has units, you’ll get a nice error message instead of compiling bogus CSS.

- To preserve quote of a string in _interpolation_, we can use `meta.inspect()` function provided by .

```css
/*-------------- SASS --------------*/
@use "sass:meta";
$font-serif: "serif","sans-serif;"

:root {
   --font-serif: #{meta.inspect($font-serif)};
}

/*-------------- CSS ---------------*/
:root {
   --font-serif: "serif", "sans-serif";
}
```

### Hidden Declarations

- Sometimes we want a property declaration to show up in a particular situation. If declaration's value is **null** or an empty **unquoted string**, **Sass** will not compile it to **CSS**.

```css
$display-block: false;

h1 {
  border: if($display-block, null, 2px) solid currentColor;
}
```

### Parent Selector

- **&** is known as **Parent selector**. It is a special selector which is used in nesting of selectors.

- **Parent Selector** makes it possible to reuse in complex ways (like adding a selector before parent, using with pseudo class & elements).

- **Parent Selector** is quite useful when we are following **BEM** methodology. We can use the selector to add **Suffixes.**

```css
/*------------------ SASS -------------------*/
.footer {
  padding: 1rem;
  display: flex;
  justify-content: space-between;

  &__navigation {
    display: flex;
    flex-direction: column;
  }

  body & {
    width: 90%;
    margin: 0 auto;
  }

  :is(&) > p {
    font-family: "Nunito", sans-serif;
  }
}

/*----------------- CSS ------------------*/
.footer {
  padding: 1rem;
  display: flex;
  justify-content: space-between;
}
.footer__navigation {
  display: flex;
  flex-direction: column;
}

body .footer {
  width: 90%;
  margin: 0 auto;
}

:is(.header, .footer) > p {
  font-family: "Nunito", sans-serif;
}
```

### Placeholder Selectors

- It is a special kind of selector in **Sass**, which looks & acts a lot like class selector.

- It starts with **%** & it's not included in **CSS** output, but it can be **extended**

- Unlike class Selectors, placeholders don't clutter up(filling a space in a disorderly way) the **CSS**.

- We can also extend **Class Selector** if needed.

```css
/* --------------- SCSS --------------- */
%text-position {
  display: flex;
  justify-content: center;
  align-items: center;

  & > * {
    color: var(--clr-gold-800);
    font-size: 2rem;
  }
}
.container {
  min-block-size: 100vh;
  display: flex;

  > * {
    flex: 1;
  }

  aside {
    @extend %text-position;
    background-color: var(--clr-gold-400);
  }

  section {
    @extend %text-position;
    background-color: var(--clr-gold-200);
  }
}

/*---------------- CSS -----------------*/
.container {
  min-block-size: 100vh;
  display: flex;
}
.container > * {
  flex: 1;
}
.container aside,
.container section {
  display: flex;
  justify-content: center;
  align-items: center;
}

.container aside > *,
.container section > * {
  color: var(--clr-gold-800);
  font-size: 2rem;
}
```

## Variables

- a **Sass** variable appears similar to **property declaration**. It starts with **$** followed by an identifier & a value is assigned to it.

- It can be declared anywhere in the **Sass** stylesheet.

```css
/*!------------- Syntax --------------*/
<variable>: <expression>;

/*!------------ Example -------------*/
$color-blue: hsl(220deg 100% 50%);

.paragraph {
  color: $color-blue;
}
```

- There are following differences between **CSS Variables** & **Sass Variables** :-

  - **Sass variables** are compiled to the value assigned to it, Where **CSS Variables** are included in css output.

  - **Sass Variables** only have one value at a time whereas **CSS Variables** can have different values for different elements.

  - **Sass variables** are _imperative_, which means if you use a variable and then change its value, the earlier use will stay the same. **CSS variables** are _declarative_, which means if you change the value, it’ll affect both earlier uses and later uses.

- **Sass Variables** like all **Sass Identifiers**, treat _hypen(-)_ & _underscore(\_)_ as identical.

- **Sass** provides a `!default` flag, which assigns a value to a variable only if that variable is not defined or its value is `null`, Otherwise the existing value will be used.
