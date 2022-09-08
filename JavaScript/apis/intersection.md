# [Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API)

- Used to observe intersection of a target element (asynchronously) with an ancestor or with a top-level document's **viewport**.
- It is initialized using `IntersectionObserver` constructor, which takes two arguments:-

  - callback function to execute
  - options (optional) in form of object

- **callback** function takes a list of `IntersectionObserverEntry` objects and the `observer`.
- **options** has 3 properties which are _root, rootMargin, threshold_.
- `root` is the ancestor or document's viewport(default) which is used as reference to observe target element.
- `rootMargin` is used to provide margin around the `root`.
- `threshold` takes a number/an array of numbers indicating percentage of the target's visibility where the observer's callback should be executed.

```js
const targetEle = document.querySelector("p");
const options = {
  root: document.querySelector("section"),
  rootMargin: "0px",
  threshold: [0.25, 0.5, 0.75]
};

const observer = new IntersectionObserver(entries => {
  entries.forEach(entry => {
    if (entry.isIntersecting && entry.target.intersectionRatio > 0.25) {
      console.log("123");
    }
  });
}, options);

observer.observe(targetEle);
```

- To unobserve an element we use `unobserve()` method on `observer` object.
