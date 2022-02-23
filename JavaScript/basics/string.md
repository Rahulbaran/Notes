# [STRING](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

- It is a primitive data type but we can also create `String` object

- String can be created as **primitives** using string literals (single quote, double quote & template literal and type - string) or as **objects** using `String()` constructor(type - object).

```js
const stringLiteral = `I am String Literal`;
const stringObject = new String("I am String Object");
```

- To use `String` object methods , Javascript automatically puts wrapper around **string literal** to treat it as `String` object.

- With `eval()`, `String` object & **string literal** show different behaviours.

```js
const strLiteral = "6 * 5";
const strObject = new String("6 * 5");

console.info(eval(strLiteral), eval(strObject)); // 11, "6 * 5"
```

- To get a primitive value from a `String` object, we use `valueOf()`.

```js
const strObj = new String("String Object");
const strLit = strObj.valueOf();
console.log(typeof strObj, typeof strLit); // object string
```

### Characters Access

- To access indivisual character of a string we can either use `charAt()` method or **ES6** approach to treat the string as an array like object.

```js
const str = "I am String";

str.charAt(5); // Returns S
str[6]; // Returns t
```

- `charAt(index)`(default index is 0) returns an empty string if character is not found whereas using **[]** returns `undefined`.

### Long Literal Strings

- There are three ways to write long literal strings.

```js
// Method 1
const concatStr =
  "Hello I am Rahul " + "I love playing kabbadi. " + "And who are you???";

// Method 2 - Using  escape character (\)
const escapeStr =
  "Hello I am Rahul \
I love playing kabaddi.";

// Method 3 - Using template literal
const templateStr = `Hello I am Rahul 
I love playing kabaddi.`;
```

### Compare Strings

- `>` & `<` operators are used for comparing strings.
- To compare in case-sensitive way, we use `==`(type corecion) or `===`.
- `localeCompare()` method can also be used for comparison.

## Constructor

### String()

- Creates a new `String` object.
- Performs type conversion when called as a function.

```js
const str = new String("fsadf");

// Performs type conversion
String(true);
```

- There are two category of methods associated with an Constructor :-
  1. Static Methods (Can only be accessed by Constructor)
  2. Instance Methods (Can be accessed by Instance)

## Static Methods

- Methods which can **only** be accessed by a class constructor (without using `prototype` property) rather than its instance.
- There are following static methods:-
  1. `String.fromCharCode()`
  2. `String.fromCodePoint()`
  3. `String.raw()`

## Instance properties

- `String.prototype.length` - Returns `length` of a string

## Instance Methods

- Methods which can be accessed by a **constructor** using `prototype` and by an instance directly using dot(.) notation.
- There are following instance methods:-

---

### trim functions

- **trim()**, **trimStart()** and **trimEnd()** methods remove white spaces from a string.
- **trim()** removes white spaces from both start & end.
- **trimStart()** removes white spaces from start.
- **trimEnd()** removes white spaces from end.
- **trimStart()** is alias of **trimLeft()** whereas **trimEnd()** is alias of **trimRight()**.
- all these methods return a string with white spaces removed.

### toUpperCase() & toLocaleUpperCase()

- Returns a string converted into **uppercase** without affecting the original string.
- **toLocaleUpperCase()** is based on **Locale (a particular place)**
- Both are prototype methods. (`String.prototype.<method>`).
- Throws **TypeError**, if element is not of type string.

### toLowerCase() & toLocaleLowerCase()

- Returns a string converted into **lowercase** without affecting the original string.
- **toLocaleLowerCase()** is based on **Locale (a particular place)**
- Both are prototype methods. (`String.prototype.<method>`).
- Throws **TypeError**, if element is not of type string.
