# [Sass(Syntactically Awesome Style Sheet)](https://sass-lang.com/documentation)

- A CSS Preprocessor (a stylesheet language) which is compiled to CSS.

- A Preprocessor is a program which takes input & produces output which is used as input by another program.

- It helps keep large stylesheets well-organized & makes it easy to share design within & across projects.

- It supports two different syntaxes:-

  1. **SCSS(Sassy CSS)** - It uses file extension `.scss`. It is a superset of CSS which means **all valid css is valid scss as well**.

  ```bash
    @mixin flex($just,$align) {
        display:flex;
        justify-content:$just;
        align-items:$align;
    }
  ```

  2. **The Indented Syntax** - It is based on Indentation rather than block and uses file extension `.sass`. It is sometimes called **Sass** because of extension.

  ```bash
    @mixin flex($just,$align)
        display:flex;
        justify-content:$just;
        align-items:$align;

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

```bash
/*-------------- SCSS -------------*/
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

```bash
/*--------------- SCSS ---------------*/
.header, .footer {
   span, h3 {
      font-family: 'Roboto',sans-serif;
   }
}

/*-------------- CSS ---------------*/
.header span, .header h3,
.footer span, .footer h3 {
   font-family: 'Roboto',sans-serif;
}
```

- We can also nest selectors which use **combinators**.

```bash
/*------------ SCSS -------------*/
.card {
   > div {
      margin-top: 1rem;
   }
}

.card + {
    .card {
      margin: .5rem 0;
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
   margin: .5rem 0;
}
h1 ~ p{
   font-size: 1.1rem;
}
```

### Interpolation

- It is used to inject **expressions** like variables, functions calls into a selector.
- It is very useful while writing **mixinx** because it allows creating selectors from the parameters passed in.

```bash
/*------------ SCSS -------------*/
@mixin define-margin($size,$value) {
   .m-#{$size} {
      margin: #{$value} + "px";
   }
}
@include define-margin(4,4);
@include define-margin(6,6);
@include define-margin(8,8);

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

-
