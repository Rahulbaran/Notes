# [CSS Custom Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)

- Multiple **Fallback Values** can be provided in `var()` function.

- **Fallback Values** are not used to fix the _browser compatibility_. If the browser does not support **CSS Custom Properties**, the fallback value will not help. It's just a backup for the browser which supports CSS custom properties to choose a different value if the given variable isn't defined or has an invalid value.
