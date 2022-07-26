# [STRING](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)

- It is a primitive data type but we can also create `String` object.

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

- To access individual character of a string we can either use `charAt()` method or **ES6** approach to treat the string as an array like object.

```js
const str = "I am String";

str.charAt(5); // "S"
str[6]; // "t"
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

## > Constructor

#### String()

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

## > Static Methods

- Methods which can **only** be accessed by a class constructor (without using `prototype` property) rather than its instance.
- There are following static methods:-
  1. `String.fromCharCode()` - Returns a **string** created using the **character codes** passed.
  2. `String.fromCodePoint()`
  3. `String.raw()`

## > Instance properties

- `String.prototype.length` - Returns `length` of a string

## > Instance Methods

- Methods which can be accessed by a **constructor** using `prototype` and by an instance directly using dot(.) notation.
- There are following instance methods:-

#### 1. trim functions

- `trim()`, `trimStart()` and `trimEnd()` methods remove white spaces from a string.
- `trim()` removes white spaces from both start & end.
- `trimStart()` removes white spaces from start.
- `trimEnd()` removes white spaces from end.
- `trimStart()` is alias of `trimLeft()` whereas `trimEnd()` is alias of `trimRight()`.
- all these methods return a string with white spaces removed.

```js
const spaceString = " Rahul Kumar Baranwal ";
spaceString.trim(); // "Rahul Kumar Baranwal"
spaceString.trimLeft(); // "Rahul Kumar Baranwal "
spaceString.trimRight(); // " Rahul Kumar Baranwal"
```

#### 2. toUpperCase() & toLocaleUpperCase()

- Returns a string converted into **uppercase** without affecting the original string.
- `toLocaleUpperCase()` is based on **Locale (a particular place)**
- Both are prototype methods. (`String.prototype.<method>`).
- Throws `TypeError`, if element is not of type string.

```js
const letters = "convert me into uppercase";
letters.toUpperCase(); // "CONVERT ME INTO UPPERCASE"
```

#### 3. toLowerCase() & toLocaleLowerCase()

- Returns a string converted into **lowercase** without affecting the original string.
- `toLocaleLowerCase()` is based on **Locale (a particular place)**
- Both are prototype methods. (`String.prototype.<method>`).
- Throws `TypeError`, if element is not of type string.

```js
const letters = "Convert Me Into uppercase";
letters.toLowerCase(); // "convert me into uppercase"
```

#### 4. at(index)

- Returns the character at the specified `index`.
- Accepts (-)ve & (+)ve integers both as argument.
- If `index` is not passed then first character is returned.
- If no character is found at specified `index` then `undefined` is returned.

```js
const str = "Get character";
str.at(-1); // "r"
str.at(4); // "c"
str.at(20); // undefined
```

#### 5. charCodeAt(index)

- Returns UTF-16 code unit value of the character at the given `index`.
- If `index` is not passed then character code of _first character_ is returned.
- If there is no character at the provided `index` then `NaN` is returned.

```js
const characters = "utf-16 characters code";
characters.charCodeAt(5); // 54
characters.charCodeAt(); // 117
characters.charCodeAt(100); // NaN
```

#### 6. charAt(index)

- Returns the character at the specified `index`.
- If `index` is not passed then first character is returned.
- If no character is found at the specified `index` then `charAt()` returns **an empty string**.

```js
const characters = "string can be created using String constructor";
characters.charAt(); //"s"
characters.charAt(1); //"t"
characters.charAt(-4); // ""
```

#### 7. concat(str, [, ...strN])

- Combines text of two or more strings & returns a new string.

#### 8. includes(searchString, [, position])

- Checks if a string contains `searchString`.
- `position` argument tells the _javascript engine_ to start searching `searchString` at mentioned position.
- `includes()` is case-sensitive.
- returns boolean value (`true/false`).

#### 9. startsWith(searchString, position)

- Determines whether **string** begins with `searchString` & returns a **boolean**.
- `position` fixes the index at which `searchString` is searched (default value is 0).
- Returns `false` if no argument is passed.
- Returns `true` if empty string is passed as `searchString`.

```js
const string = "Hello Ram Ji kaise ";
string.startsWith("H"); // true
string.startsWith("a"); // false
string.startsWith("a", 7); // true
string.startsWith(); // false
```

#### 10. endsWith(searchString, length)

- Determines whether a **string** ends with `searchString`.
- `length` is used as length of **string**.
- Returns `false` if no argument is passed.
- Returns `true` if empty string is passed as `searchString`.

```js
const string = "Hello Ram Ji Rab ne Bana Di Jodi";

string.endsWith("Jodi"); // true
string.endsWith("Jod", str.length - 1); // true
string.endsWith("J"); // false
string.endsWith("od", str.length); // false
```

#### 11. indexOf(searchValue [, fromIndex])

- Returns the index of first occurrence of `searchValue` in the `String` object.
- Returns `-1` if it is not found.
- If no `searchValue` is passed then it returns `-1`.
- `fromIndex` (optional) fixes a position after which `searchValue` is looked for.

```js
const str =
  "Map is new data structure introduced in JavaScript ES6 & It was created using Map Constructor";

str.indexOf("M"); //0
str.indexOf(); // -1
str.indexOf("i", 5); // 26
str.indexOf("x"); // -1
```

#### 12. lastIndexOf(searchValue [, fromIndex])

- Returns **index** of **last occurence** of `searchValue` in the given string.
- Returns `-1` if `searchValue` is not found in the string.
- If `searchValue` is not found in the string then `-1` is returned.

```js
const str = "JUMBO SIZE SOFTBOUND NOTE BOOK";
str.lastIndexOf("O"); // 28
str.lastIndexOf(); // -1
str.lastIndexOf("ram"); // 1
```

#### 13. slice(beginIndex, endIndex)

- Extract substring(a section) from the given string & returns it.
- Takes `beginIndex` & `endIndex` as arguments (both are optional).
- indexes can be (-)ve & (+)ve both.
- If both `beginIndex` & `endIndex` are either (+)ve or (-)ve then `endIndex` should always be greater than `beginIndex` to get a **substring** of `length` greater than 0.
- If both `beginIndex` & `endIndex` are same then an empty string is returned.
- In case of passing `endIndex`, character on that index position is not included in the returned substring.
- If no indexes are passed then whole string is returned.

```js
const sliceStr =
  "slice() is used to slice & return a section of string without affecting the actual string";

sliceStr.slice(0, 2); // "sl"
sliceStr.slice(-5, -1); // "trin"
sliceStr.slice(0, -1); // whole string except last character
sliceStr.slice(-1); // "g"
sliceStr.slice(); // whole string
sliceStr.slice(0, 0); // ""
```

#### 14. replace(searchFor, replaceWith)

- Returns a string with `searchFor` is replaced with `replaceWith`.
- `searchFor` can either be a **string** or a **Regular Expression**.
- `replaceWith` can be either a **string** or a **function**.

#### 16. split(separator, limit)

- Returns an array of substrings after splitting a **String** based on `separator` passed.
- `separator` can either be a simple **string** or a **regular expression**.
- It `separator` is omitted or not found in the **String** then returned array contains one element which is entire string.
- If `separator` is an empty string("") then returned array contains each of UTF-16 characters of **String**.
- `limit` is any non-negative integer which stops the entries in array after `limit`.

## > HTML Wrapper Methods

#### 1. anchor(arg)

- These wrapper methods are **deprecated**.

- Returns a string containing `<a>` tag & `arg` as `name` attribute if it is passed in `anchor()` otherwise `undefined` is used as `name`.

```js
const string = "Download Now";
string.anchor("book"); // "<a name=\"book\">Download Now</a>"
```

#### 2. big()

- Returns a string containing `<big>` tag.

```js
const string = "Big letters";
string.big(); // "<big>Big letters</big>"
```

#### 3. blink()
