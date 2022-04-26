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

### > Methods Used in Regular Expressions.

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

- We can use **g** flag to include capture groups along with matc.

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

- `pattern` can be either a string or a `RegExp` whereas `replacement` can either be a **string** or a **callback function**.

##### Syntax

```js
// PATTERN - STRING/REGEX, REPLACEMENT - STRING/FUNCTION
replace(pattern, replacement);
```

- We use **g(global)** flag in `RegExp` to replace all the matches with `replacement`.

- Examples:-

```js
const string = "My mummy is one of the best mummy in world";

string.replace("mummy", "papa"); // My papa is one of the best mummy in world
string.replace(/mummy/g, "papa"); // My papa is one of the best papa in world
string.replace(new RegExp("mummy", "g"), "papa"); // My papa is one of the best papa in world
```

##### Syntax for callback function:-

```js
function replacer(match, p1, p2, ...pn, offset, string) {}
/*
* match - Matched substring
* p1, p2, ...pn - captured groups
* offset - offset of the matched substring within the whole string
* string - The whole string being examined
*/
```

#### replaceAll()

- Returns a new string with replacing all the matches of a `pattern` with a `replacement`.

- Similar to `replace()`, `pattern` can either be a **string** or a **regular expression** whereas `replacement` can be a **string** or a **callback function**.

- While using **regular expression** as `pattern` in `replaceAll()`,`g` flag is must.

- Examples:-

```js
const parents = "I love parents more than I do love god";
const regex = /(parents|god)/g;

const replacer = match => {
  return match === "parents" ? "god" : "parents"; //I love my god more than I do love parents
};

parents.replaceAll(regex, replacer); //
```

#### search()

- Instance method of **String**.

- Used for searching a `pattern` in the given string and returns **index of first match** if match is found otherwise returns **-1**.

- Takes a `RegExp` object as argument(`pattern`). If non-RegExp object is passed then it is **implicitly** coverted into a `RegExp` with `new RegExp(regexp)`.

```js
const str = "The fox jumps from the bed to sky hola!";
const pattern = /[^\w\s]/g;

str.search(pattern); // 38
```

#### split()

- Instance method of **String**(associated with **prototype** property).

- Returns an array containing an ordered list of substrings after dividing the string based on a pattern passed as in **split()**.

- Syntax:-

```js
split(separator, limit);

/*
 * both arguments separator & limit are optional.
 * separator can be a simple string or a regular expression.
 * limit is used to limit number of substrings returned.
 * By default (when separator is not mentioned) the returned array contains the entire string.
 */
```

---

### > Special Characters

- There is a bunch of _special characters_ used in **regular expression** and they belong from different categories

##### 1. Assertions

- They include **boundaries** which indicate beginnings & endings of lines & words and other patterns.

##### 2. Character classes

- Used to distinguish different types of characters.

##### 3. Groups and ranges

- They indicate **groups & ranges** of expression characters.

##### 4. Quantifiers

- Indicates number of characters or expressions to match.

##### 5. Unicode property escapes

- Distinguish based on unicode character properties.

---

### > Table Containing Special Characters

| CHARACTERS/CONSTRUCTS                                                                      | CORRESPONDING ARTICLE    |
| ------------------------------------------------------------------------------------------ | ------------------------ |
| **`\, ., \cX, \d, \D, \f, \n, \r, \s, \S, \t, \v, \w, \W, \0, \xhh, \uhhh, \uhhhh, [\b]`** | Character Classes        |
| **`^, $, x(?=y), x(?!y), (?<=y)x, (?<!y)x, \b, \B`**                                       | Assertions               |
| **`(x), (?:x), (?<Name>x), [xyz], [^xyz], \Number`**                                       | Groups and ranges        |
| **`*, +, ?, x{n}, x{n, }, x{n,m}`**                                                        | Quantifiers              |
| **`\p{UnicodeProperty}, \P{UnicodeProperty}`**                                             | Unicode property escapes |

---

### > Advance Searching with flags

| FLAG    | DESCRIPTION                                              | Corresponding Property        |
| ------- | -------------------------------------------------------- | ----------------------------- |
| **`g`** | Global Search                                            | `RegExp.prototype.global`     |
| **`i`** | Case-sensitive Search                                    | `RegExp.prototype.ignoreCase` |
| **`m`** | Multi-line Search                                        | `RegExp.prototype.multiline`  |
| **`s`** | Allows **wild character(.)** to match newline characters | `RegExp.prototype.dotAll`     |
| **`d`** | Generates indices for substring matches                  | `RegExp.prototype.hasIndices` |
| **`u`** | Treats a pattern as a sequence of unicode code points    | `RegExp.prototype.unicode`    |
| **`y`** | Performs a _sticky_ match                                | `RegExp.prototype.sticky`     |

---

### > All Types of Special Characters

#### 1. Assertions

| Characters    | Meaning                                                                                                                                                          |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`^`**       | Matches _begining_ of input. In case of multiline flag set(m), matches also occurs after a line break. It has different meaning when used in **character class** |
| **`$`**       | Matches _end_ of input, In case of multiline flag set(m), matches also occurs after a line break                                                                 |
| **`\b`**      | Matches a _word boundary_. This is the position where a word character is not _followed/preceded_ by another word-character                                      |
| **`\B`**      | Matches a _non-word boundary_. A position where the previous & next character are of same type.                                                                  |
| **`x(?=y)`**  | **Lookhead assertion:** Matches _x_ only if **`x`** is _followed_ by **`y`**                                                                                     |
| **`x(?!y)`**  | **Negative lookhead assertion:** Matches **`x`** only if **`x`** is _not followed_ by **`y`**                                                                    |
| **`(?<=y)x`** | **Lookbehind assertion:** Matches **`x`** only if **`x`** is _preceded_ by **`y`**                                                                               |
| **`(?<!y)x`** | **Negative lookbehind assertion:** Matches **`x`** only if **`x`** is _not preceded_ by **`y`**                                                                  |

#### 2. Character classes

| Characters | Meaning                                                                                                                                                 |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`.`**    | Matches any single character expect line terminators: **`\n, \r, \u2028 or \u2029`**. **dot(.)** looses its special behavior inside **character class** |
| **`\d`**   | Matches a **single digit**. It is equivalent to **[0-9]**                                                                                               |
| **`\D`**   | Matches any character which is **not a digit**. It is equivalent to **[^0-9]**                                                                          |
| **`\w`**   | Matches any **alphanumeric character along with underscore**. It is equivalent to **[A-Za-z0-9_]**                                                      |
| **`\W`**   | Matches any single character **except alphanumeric character & underscore**. It's equivalent to **[^a-za-z0-9_]**                                       |
| **`\s`**   | Matches any **single white space character** including space, tab, form feed, line feed & other Unicode spaces                                          |
| **`\S`**   | Matches any **single character other than white space**.                                                                                                |
| **`\t`**   | Matches a horizontal tab                                                                                                                                |
| **`\r`**   | Matches a carriage return                                                                                                                               |
| **`\n`**   | Matches a linefeed                                                                                                                                      |
| **`\v`**   | Matches a vertical tab                                                                                                                                  |
| **`\f`**   | Matches a form feed                                                                                                                                     |
| **`[\b]`** | Matches a **backspace**                                                                                                                                 |
| **`\0`**   | Matches a **NULL** character                                                                                                                            |
