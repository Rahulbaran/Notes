# [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

- `Array` object can contains a mix of different `data types`.
- **Arrays** are not associative which means **elements can not be accessed using strings as indexes**.

## Constructor

#### Array()

- Creates a new `Array` object.

## Static Methods

#### Array.from()

- Creates a new `Array` instance from an array-like object or iterable object.

#### Array.isArray()

- Returns `true` if argument is an array otherwise returns `false`.

#### Array.of()

- Creates an array with a number of arguments passed.

```js
// Syntax
Array.of(ele1, ...eleN);

//Example
const newArray = Array.of(1, 2, 3, 4, 5); //[1,2,3,4,5]
```

## Instance Properties

#### Array.prototype.length

- Returns the number of elements in an array.

## Instance Methods

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

#### entries()

- Returns a new `array iterator` object which contains **key/value** pair for each index in an array.

```js
const gymDay = ["Biceps", "Shoulder", "Chest", "Back", "Triceps", "Leg"];
for (let entry of gymDay.entries()) {
  console.log(entry);
}
```

#### keys()

- Returns a new `array iterator` object which contains **keys** for each index in the array.

```js
const states = ["Jharkhand", "Bihar", "Uttar Pradesh", "Telangana", "Punjab"];
for (let key of states.keys()) {
  console.log(key);
}
```

#### values()

- Returns a new `array iterator` object which contains **values** for each index in the array.

```js
const members = ["Sun", "Mon", "Tue", "Wed", "Thur", "Fri", "Sat"];
for (let member of members.values()) {
  console.log(member);
}
```

#### shift()

- Removes an element from beginning of an array & returns it.
- If there is no element in the array then `undefined` is returned.

#### unshift()

-

#### slice()

- Returns a **shallow copy** of a portion of an array based on `start` & `end` indexes.
- element on `end` index is not included in the new array.
- Takes **(-)ve** & **(+)ve** numbers both as indexes.
- If `start` & `end` are not provided then whole array is returned.

```js
const account = {
  account_holder: "Rahul Kumar",
  account_no: 525110110008571,
  transactions: [1200, -1455, -25000, 9000, 15500]
};

account.transactions.slice(); // [1200, -1455, -25000, 9000, 15500]
account.transactions.slice(0); // [1200, -1455, -25000, 9000, 15500]
account.transactions.slice(0, account.transactions.length - 1); // [1200, -1455, -25000, 9000]
account.transactions.slice(0, -2); // [1200, -1455, -25000]
account.transactions.slice(-1); // [15500]
```

#### splice()

- Changes the contents of an array by removing/replacing existing elements and/or adding new elements.

- Returns an array containing deleted elements.

- **Syntax**

```js
splice(start)
splice(start, deleteCount)
splice(start, deleteCount, item1)
splice(start, deleteCount, item1, ...., itemN)
```

- **Examples**

```js
const cgpa = [7.63, 7.29, 7.77, 7.7, 8, 8.24, 7.79];

cgpa.splice(5, 0, 7.95); // []
cgpa.splice(5, 1); // [7.95]
cgpa.splice(2, 0, 7.54); // []
cgpa.splice(-3, 1); // [8]
```

#### concat()

- Merges two or more arrays without changing the existing arrays.

```js
const cgpa = [7.63, 7.29, 7.77, 7.7, 8, 8.24, 7.79];
const marks = [340, 310, 360, 355, 400, 410, 360];

cgpa.concat(335, 353, marks); // [7.63, 7.29, 7.77, 7.7, 8, 8.24, 7.79, 335, 353, 340, 310, 360, 355, 400, 410, 360]
```

#### sort()

-

#### toLocaleString()

-

#### toString()

-

#### fill()

-

#### find()

-

#### every()

-

#### findIndex()

-

#### flat()

-

#### flatMap()

-

#### forEach()

- Executes a provided function (callback/arrow function) once for each array element.

- We can't use `break` & `continue` keywords with `forEach()`.

- **Syntax**

```js
forEach(element => {});
forEach((element, index) => {});
forEach((element, index, array) => {});

forEach(callbackFn);
forEach(callbackFn, thisArg);
```

#### includes()

-

#### indexOf()

-

#### lastIndexOf()

-

#### join()

- Joins all the elements of an **array** into a string based on specified separator string (default - **comma(,)**).
- If `length` of array is **0** then _empty string_ is returned.

```js
const bodyElements = ["Fire", "Space", "Water", "Earth", "Air"];

bodyElements.join("<-->");
```

#### map()

-

#### reduce()

-

#### reverse()

- Reverse the original array & returns it.

```js
const gymMembers = ["Satish", "Ranjit", "Uttam", "Shubham"];
gymMembers.reverse(); // ['Shubham', 'Uttam', 'Ranjit', 'Satish']
```

#### filter()

- Returns a new array with all elements that pass the test implemented by the provided function.

- The provided function is invoked with 3 arguments **element, index & array**.

- It also takes an optional arugment as `thisArg` which contains the `this` value used by provided function.

```js
const numbers = [4, 3, 5, 6, 1, 7, 8];
const evenNumbers = numbers.filter(function (num) {
  console.log(this);
  return num % 2 === 0;
});
console.log(evenNumbers); // [4,6,8]

const nums = [-1, -2, 0, 40, 12, 3];
const positiveNumbers = numbers.filter(function (num, index, array) {
  return num >= 0;
});
console.log(positiveNumbers); // [0, 40, 12, 3]
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
