#### push(element)

- Push an element at last of an array & returns its `length`.
- If no element is passed & array's length is 0 then **0** as `length` is returned.

```js
const certificates = ["Ojass", "Sandhaan"];
certificates.push("Sabse Acha Baccha"); // length - 3
certificates.push(); // length - 0
```

#### pop()

- Removes an element from the last position & returns it.
- Returns `undefined` if there is no element in the array.

```js
const skills = [
  "HTML",
  "CSS3",
  "JavaScript",
  "Sass",
  "React",
  "Flask",
  "MySQL",
  "MongoDB"
];
skills.pop(); // "MongoDB"

const interests = [];
interests.pop(); // undefined
```

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

#### at(index)

- Returns the value at the specified `index`.
- Accepts (-)ve & (+)ve integers both as argument.
- If `index` is not passed then first value is returned.
- If no value is found at specified `index` then `undefined` is returned.

```js
const members = ["Bhai", "Sister", "Mummy", "Papa"];
members.at(-1); // "Papa"
members.at(6); // undefined
members.at(); // "Bhai"
```
