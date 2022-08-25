# Window sizes & scrolling

- To get info like _width & height of the browser window_, _full width & height of the document(including scrolled out part)_, we use root document element `document.documentElement`.
- `document.documentElement` is the root document element in the browser.

```js
// For HTML
document.documentElement === document.querySelector("html");
```

### Width/height of the window

- To get window width & height, we can use `clientWidth` & `clientHeight` respectively(both are readonly).
- **scrollbar in window** is excluded while calculating both width & height.

```js
const root = document.documentElement;
console.log(root.clientHeight, root.clientWidth);
```

> `window.innerWidth/innerHeight` also includes the scrollbar while calculating width & height.

### Width/height of the document

- We use `scrollWidth/scrollHeight` properties of `document.document.documentElement` to get the document's full size.
- Sometimes `scrollWidth` & `scrollHeight` don't work as expected, So to get a reliable document size, we should take maximum of following properties:

```js
const [$root, $body] = [document.documentElement, document.body];
const scrollHeight = Math.max(
  $root.scrollHeight,
  $body.scrollHeight,
  $root.clientHeight,
  $body.clientHeight,
  $root.offsetHeight,
  $body.offsetHeight
);
```

### Get the current scroll

- `scrollLeft/scrollTop` properties contain current scroll state of DOM elements.
- `document.documentElement.scrollLeft/scrollTop` works in most browsers except older Webkit-based ones where we should ue `document.body` instead of `document.documentElement`.

> `window.scrollX`, `window.pageXOffset` & `scrollLeft` are aliases also `window.scrollY`, `window.pageYOffset` & `scrollTop` are aliases.

### Scrolling: scrollTo, scrollBy, scrollIntoView

- Regular elements/page can be scrolled by changing `scrollTop/scrollLeft`.
- Special methods `window.scrollBy(x, y)` & `window.scrollTo(pageX, pageY)` can also be used to scroll the page.
- `window.scrollBy(x, y)` scrolls the page _relative to its current position_.
- `window.scrollTo(pageX, pageY)` scrolls the page to `absolute coordinates`.(Similar to setting `scrollLeft/scrollTop`).

#### scrollIntoView

- `ele.scrollIntoView(top)` scrolls the page to make `ele` visible.
- If `top=true`(defualt) then page will be scrolled to make `ele` appear on the top whereas `top=false` make the page to scroll to make `ele` appear at the bottom.

# Element size & scrolling

### offsetParent, offsetLeft/Top

- These are **most outer** geometry properties.
- `offsetParent` is the nearest ancestor that browser uses for calculating coordinates while rendering.
- `offsetLeft/offsetTop` provide x/y coordinates relative to `offsetParent` upper-left corner.

### offsetWidth/Height

- It provides the full size (width/height) of the element(including borders).
- `offsetWidth`= contentWidth + paddings(inline) + borders(inline)
- `offsetHeight`= contentHeight + paddings(block) + borders(block)

### clientTop/Left

- These properties are used to calculate relative coordinates of the inner side from outer side(excluding border & scrollbar).

### clientWidth/Height

-
