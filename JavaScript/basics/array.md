#### shift()

- Removes an element from beginning of an array & returns it.
- If there is no element in the array then `Undefined` is returned.

#### filter()

- An Instance method of Array.
- Returns a new array with all elements that pass the test implemented by the provided function.

```js
const numbers = [4, 3, 5, 6, 1, 7, 8];
const evenNumbers = numbers.filter(function (num) {
  console.log(this);
  return num % 2 === 0;
});
console.log(evenNumbers); // [4,6,8]
```
