# CSSOM(CSS Object Model) API

## CSSStyleSheet

- `CSSStyleSheet` interface repersents a single `CSS` stylesheet & allows use inspect & modify the list of rules contained in the stylesheet.
- Inherits properties & methods from its parent, `StyleSheet`.
- `cssRules` property returns rules contained in a `CSSRuleList`.

> `document.styleSheets` returns `StyleSheetList` object which contains a no. of `CSSStyleSheet` objects.

### Constructor

- `CSSStyleSheet()`

### Properties

- properties are inherited from `StyleSheet`.

##### CSSStyleSheet.cssRules

- Returns a live `CSSRuleList` object which contains `CSSRule` objects.

##### CSSStyleSheet.ownerRule

## StyleSheet
