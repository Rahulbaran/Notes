### :is()

- Pseudo Class Selector

- Takes a list of selectors as arguments and applies styles to any child element of the selectors.

- It's **specificity** is equivalent to specificity of the elements supplied in it.

- useful for writing large selectors in a more compact form

- **Pseudo-elements** are not valid in the selector list for :is().

- For older & legecy browsers, we also use **:matches()** & **:-webkit-any() and :-moz-any()** along with **:is()**.

### :where()

- A Pseudo Class Selector which has similar feature as `:is()`.

- It always has **specificity** equal to zero and in this perspective it is different from `:is()` which takes **specificity** of the selectors passed in it.

- When using `:is()` or `:where()` instead of the whole list of selectors being **deemed invalid** if one fails to parse, the incorrect or unsupported selector will be **ignored** and the others used.

### :not()

- Pseudo Class Selector
