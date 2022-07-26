# [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

- `Array` object can contains a mix of different `data types`.
- **Arrays** are not associative which means **elements can not be accessed using strings as indexes**.

## Constructor

#### Array()

- Creates a new `Array` object.

## Static Methods

#### Array.from()

- Creates a new `Array` instance from an **array-like object or iterable object**.
- We can also use a **map function** in `Array.from()`.
- **Syntax**

```js
// Arrow Function
Array.from(arrayLike, element => {});
Array.from(arrayLike, (element, index) => {});

// Mapping Function
Array.from(arrayLike, mapFn);
Array.from(arrayLike, function mapFn(element) {});
Array.from(arrayLike, function mapFn(element, index) {});
```

- **Example**

```js
// From a String
Array.from("array"); // ['a', 'r', 'r', 'a', 'y']

// From a Set
Array.from(new Set(["Ram", "Laxman", "Sita"])); // ['Ram', 'Laxman', 'Sita']

// From a Map
const map = new Map([
  [0, "Mummy"],
  [1, "Papa"],
  [2, "Malti"],
  [3, "Rohit"]
]);
Array.from(map); // [[0, 'Mummy'], [1, 'Papa'], [2, 'Malti'], [3, 'Rohit']]
Array.from(map.keys()); // [0,1,2,3]
Array.from(map.values()); // ['Mummy', 'Papa', 'Malti', 'Rohit']

// From a NodeList
const subHeadings = document.querySelectorAll("h3");
Array.from(subHeadings, sub => sub.textContent);

// From Array-like objects (arguments)
const f = function () {
  return Array.from(arguments);
};
f(10, 20, 30); // [10, 20, 30]

// Using Arrow Function & Array.from()
Array.from({ length: 5 }, (v, i) => i); // [0,1,2,3,4]
```

#### Array.isArray()

- Returns `true` if argument is an array otherwise returns `false`.
- **Example**

```js
const notes = [5, 10, 20, 50, 100, 200, 500, 2000];
Array.isArray(notes); // true
```

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
- **Syntax**

```js
push(element);
push(element1, element2, ....., elementN);
```

- **Example**

```js
const certificates = ["Ojass", "Sandhaan"];

certificates.push("Sabse Acha Baccha"); // length ---> 3
certificates.push(); // length ---> 0
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

- Elements of an array are sorted by **converting them into strings** & then **comparing their sequences of UTF-16 code units values** and sorted array is returned.
- Instead of creating a copy, original array is sorted.
- If **callback/arrow function(compareFn)** is used to sort the array then all non-`undefined` elements are sorted according to the return value of the compare function (**without converting elements into string**).
- **Syntax**

```js
sort();
sort((a, b) => {});
sort(compareFn);
sort(function (a, b) {});
```

| compareFunction(a, b) return value | sort order                       |
| ---------------------------------- | -------------------------------- |
| > 0                                | sort `b` before `a`              |
| < 0                                | sort `a` before `b`              |
| === 0                              | keep original order of `a` & `b` |

- **Example**

```js
const numbers = [20, 4324, 13213, 213, 100];

const compareFn = (a, b) => a - b;
numbers.sort(); // [100, 13213, 20, 213, 4324]
numbers.sort(compareFn); // [20, 100, 213, 4324, 13213]
```

#### toLocaleString()

-

#### toString()

-

#### fill()

- `fill()` method changes elements in an array to a static value from a **start index(default 0)** to an **end index(default `array.length`)** & returns the array.
- **Syntax**

```js
fill(value);
fill(value, start);
fill(value, start, end);
```

```js
const numbers = [10, 30, 40, 10, 50];

const modifiedNumbers = numbers.fill(100, 3, 4).sort((a, b) => a - b);
console.log(modifiedNumbers); // [10, 30, 40, 50, 100];

numbers.fill(14, -2); // [10, 30, 40, 14, 14]
```

#### some()

- It tests if at least one element in the array passes the test implemented by provided function(**callback/arrow function**).
- provided function takes **element, index & array** as arguments.
- `true` is returned if an element is found otherwise `false`.
- **Syntax**

```js
// Arrow Function
some((element, index, array) => {});

// Callback Function
some(callbackFn);

// Inline Callback Function
some(function (element, index, array) {});
```

- **Example**

```js
const numbers = [1, 5, 3, 6, 10, 45];

numbers.some(ele => ele > 10); // true
numbers.some(ele => ele < 1); // false
```

- `includes()` tests only for **equality** whereas `some()` tests for **a condition.**

#### find()

- Takes a **callback/arrow function** & returns the _first element_ which satisfies the condition specified in the function (`truthy` value).
- If no value satisfy the condition then `undefined` is returned.
- the function takes **element, index & array** as arguments.
- `find()` also takes `thisArg` which is used as `this` inside each invocation of the **callback/arrow function**.
- **Syntax**

```js
// Arrow Function
find((element, index, array) => {});

// Callback Function
find(callbackFn);

// Inline Callback Function
find(function (element, index, array) {});
```

#### every()

- It takes a **callback/arrow function** & returns `true` if all the elements in the array passes the condition passed the function, otherwise returns `false`.
- **Syntax**

```js
// Arrow Function
every((element, index, array) => {});

// Callback Function
every(callbackFn);

// Inline Callback Function
every(function (element, index, array) {});
```

#### findIndex()

- The method takes a **testing function(callback/arrow)** and returns the **index** of first element in the array that **satisfies the condition mentioned in the function**.
- If no element is found then `-1` is returned.
- **testing function** takes `element, index & array` as arguments.
- **Syntax :-**

```js
findIndex((element, index, array) => {});
findIndex(callbackFn);
findIndex(function (element, index, array) {});
```

- **Example**

```js
const options = ["A", "B", "C", "D", "E"];
options.findIndex((ele, i, arr) => ele === "A"); // 0

options.findIndex(function (ele, i, arr) {
  ele === "F";
}); // -1
```

#### flat()

- Creates a new array with all the sub-array elements concatenated into it recursively upto the **specified depth**.
- Default **depth** is 1.
- **Syntax**

```js
flat();
flat(depth);
```

- **Example**

```js
const complexArray = [10, 20, [1, 2, 4, [4, 5, [150, 200]]]];
const simpleArray = complexArray.flat(4);
console.log(simpleArray); //[10, 20, 1, 2, 4, 4, 5, 150, 200]
```

#### flatMap()

- Returns a new array formed by applying a given **callback function** to each element of the array & then **flattening the result by one level**.
- Identical to `map()` followed by a `flat()` of depth 1 but slightly more efficient than calling those two methods separately.
- **Syntax**

```js
flatMap((element, index, array) => {});
flatMap(callbackFn);
flatMap(function (element, index, array) {});
```

- **Example**

```js
const numbers = [2, 3];
const table = numbers.flatMap(ele => [
  [ele, ele * 2, ele * 3, ele * 4, ele * 5]
]);
console.log(table); // [[2, 4, 6, 8, 10], [3, 6, 9, 12, 15]]
```

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

- Used to look for **first index** of a given element. If element is not found then `-1` is returned.
- Along with the element, it also takes **fromIndex** as argument(optional) which is the index from where element should be searched.
- **Syntax**

```js
indexOf(searchElement);
indexOf(searchElement, fromIndex);
```

- In comparison with `findIndex()`, it can be used only for searching simple values.

```js
const ar = ["Rahul Kumar Baranwal", "Dumri", 26, 825106];

ar.indexOf("Dumri", 1); // 1
ar.indexOf("Rahul Kumar Baranwal", 1); // -1
```

#### lastIndexOf()

- Used to look for **last index** of a given element. If element is not found then `-1` is returned.
- Along with the element, it also takes **fromIndex** as argument(optional) which is the index from where element should be searched.

#### join()

- Joins all the elements of an **array** into a string based on specified separator string (default - **comma(,)**).
- If `length` of array is **0** then _empty string_ is returned.

```js
const bodyElements = ["Fire", "Space", "Water", "Earth", "Air"];

bodyElements.join("<-->");
```

#### map()

- Executes a provided function (callback/arrow function) once for each array element & returns a **new array** containing results of calling the function on each element.
- Provided function is invoked upto 3 arguments **element, index & array**.
- It also takes an optional arugment as `thisArg` which contains the `this` value used by provided function.
- If Provided function does not return anything then an array containing `undefined` as values are returned.

```js
const numbers = [1, 4, 9, 16, 25];
const sqrts = numbers.map(num => Math.sqrt(num)); // [1,2,3,4,5]
```

#### reduce()

- Executes a user-supplied **reducer callback function** on each element of an array & Final result is a single value.
- The executer function takes `previousValue`, `currentValue`, `currentIndex` & `array` as arguments.
- We can also provide `initialValue`(default is 1st element of the array) as 2nd argument in `reduce()`.
- **Syntax**

```js
// Arrow Function
reduce((previousValue, currentValue, currentIndex, array) => {}, initialValue);

// Inline Callback FUnction
reduce(function (previousValue, currentValue, currentIndex, array) {},
initialValue);
```

- **Example**

```js
const numbers = [10, 20, 14, 5, 16, 10];
numbers.reduce((a, b) => a + b, 0); // 75
```

#### reduceRight()

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
- Accepts (-)ve & (+)ve integers both as `index`.
- If `index` is not passed then first value is returned.
- If no value is found at specified `index` then `undefined` is returned.

```js
const members = ["Bhai", "Sister", "Mummy", "Papa"];
members.at(-1); // "Papa"
members.at(6); // undefined
members.at(); // "Bhai"
```
