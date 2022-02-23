# [Regular Expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)

- Patterns which are used for matching character combination in **Strings**.

- _Regular Expression_ is also an **object(RegExp)**.

- These patterns are used with `exec()`, `test()` etc methods of **RegExp** object and instance methods of **String** such as `match(), matchAll(), replace(), replaceAll(), split(), search()`etc.

- We can create a regex pattern either using regular expression literal enclosed between **slashes** or using **RegExp** constructor.

```js
// Using Regular Expression Literal
const re = /<pattern>/;

// Using RegExp Constructor
const reg = new RegExp("<pattern>");
```

---

#### test()

- Instance method.
- Returns a _boolean_ value based on either pattern is found or not.

```js
const text = "Hello World I am Rahul Baran from India";
const reg = /am/;

reg.test(text); // true
```

#### exec()

- Search the specified pattern in the given string and returns **an array**(if pattern is found) or `null`.

- Returned array contains the matched substring (sometimes it also contains index, input and capturing groups).

##### Syntax

```js
exec(str);
```

- We can use **g** flag to find multiple matches in whole the string.

```js
const jsCourse = "Jonas has the best JS Course";
const [reg, regGlobal] = [/s/, /s/g];

reg.exec(jsCourse); // ["s"]
```

#### match()

- Instance method of **String**.
- Takes a **regular expression** object(pattern) as argument.
- Used to match a _string_ against a **regular expression** and returns an **array** containing **match(es)**/**empty string**.

- When **g** flag is not used then returned **array** also contains following additional properties

  1. **groups(an object of named capturing groups)**
  2. **index(index where result was found)**
  3. **input(a copy of search string)**

- If **global flag(g)** is used then we either get an **array** of **match(es)** or `null`. (capturing groups are ignored when using **g** flag).

```js
const str = "Kya haal hai bhailog aur kaise hai ghar pe sab";

// Without "g" flag
const reg = /a/;
str.match(reg); // ["a"]

// Using "g" flag
const regex = /a/g;
str.match(regex); // ["a","a","a","a","a","a","a","a","a","a","a"]

// Capturing groups (g flag should not be used)
str.match(/(a)/); // ["a", "a"]
```

#### matchAll()

- Takes `regular expression` object as argument.
- Returns an **iterator** of all _results(matches)_ including **capturing groups**.

- Each _match_ is an array (with extra properties `index` & `input`).

- We can use more convenient constructs `for...of`,`array spread` or `Array.from()` to loop the iterator.

```js
const foo = "football poolball moon";
Array.from(foo.matchAll(/f?(oo(\w+))/g)); // 3 Arrays (matches)
```

> **matchAll()** is always used with **g** flag, otherwise it will throw a `TypeError`.

#### replace()

- Returns a new string with replacing some/all matches of a `pattern` by a `replacement`.

- `pattern` can be either a string or a `RegExp` whereas `replacement` can be a string or a function to be called for each match.

- We use **g** flag in `RegExp` to replace all the matches with `replacement`.

##### Syntax

```js
replace(pattern, replacement);
```

- Examples:-

```js
const string = "My mummy is one of the best mummy in world";

// String as a pattern
string.replace("mummy", "papa"); // My papa is one of the best mummy in world

// Regular Expression with "g" Flag as pattern
string.replace(/mummy/g, "papa"); // My papa is one of the best papa in world
```

#### replaceAll()

- Returns a new string with replacing all the matches of a `pattern` with a `replacement`.
