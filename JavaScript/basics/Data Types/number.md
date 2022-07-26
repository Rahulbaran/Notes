# [Number]()

- In **JavaScript**, numbers are represented as _floating-point value_ (not an integer).
- Internally, numbers are represented in **binary format(base 2)**.
- It is difficult to convert fractions in binary format that's why sometimes, we get weird results.
- numbers can be expressed as _a literal_ or _an object_ using `Number` constructor.
- `Number()` function can be used to convert values of other type to numbers (if can't be converted then `NaN` is returned).

> We can also use **Unary Plus(+)** operator for converting value of other types to _Number_ (It does type coercion for conversion).

## Constructor

#### Number()

- Used to create **number object**.

## Static Properties

#### Number.EPSILON

- It represents the difference between 1 & the smallest floating point number greater than 1.

#### Number.MAX_SAFE_INTEGER

- Represents the maximum safe integer in JavaScript(`2^53 - 1`).
- **Value** - `9007199254740991`

#### Number.MIN_SAFE_INTEGER

- Represents the minimum safe integer in JavaScript(`-2^53 - 1`).
- **Value** - `-9007199254740991`

#### Number.MAX_VALUE

- The maximum numeric value representable in JavaScript.
- **Value** - `1.7976931348623157e+308`

#### Number.MIN_VALUE

- The minimum numeric value representable in JavaScript.
- **Value** - `5e-324`

#### Number.NaN

- Special **Not a Number** value.

#### Number.NEGATIVE_INFINITY

- It represents negative infinity and it is returned on overflow.

#### Number.POSITIVE_INFINITY

- It represents infinity and it is returned on overflow.

#### Number.prototype

- Allows the addition of properties to the `Number` object.

## Static Methods

#### Number.isNaN()

- Checks whether the passed value is `NaN` and returns a boolean value.
- _Type Conversion(Coercion)_ is done (whenever required) before checking for `NaN`.
- **Example**

```js
Number.isNaN(20); // false
Number.isNaN(NaN); // true
Number.isNaN("20G"); // true
Number.isNaN("20" / "4E"); // true
```

> Global `isNaN()` has same functionality as `Number.isNaN()`.

#### Number.isFinite()

- Checks whether the passed value is a finite number(a countable number less than infinity).
- **Example**

```js
Number.isFinite(4 / 0); // false
Number.isFinite(1 / "4f"); // false
Number.isFinite(10 / 43); // true
```

> Global `isFinite()` has same functionality as `Number.isFinite()` except it does _Type Coercion_ unlike the later one.

#### Number.isInteger()

- Checks whether the passed value is an integer & returns a boolean value.
- It does not do _Type Coercion_ before checking.

#### Number.isSafeInteger()

- Checks whether the passed value is a _safe integer_(number between `-(2^53 - 1)` & `2^53 - 1`).
- **Example**

```js
Number.isSafeInteger(Math.pow(2, 53) - 1); // true
Number.isSafeInteger(Math.pow(2, 53)); // false
```

#### Number.parseFloat()

- Parses an argument & returns a floating point number. If argument can't be parsed then `NaN` is returned.
- Passed argument should be a string, if not then it is converted to one using `ToString` abstract operation.
- **Syntax**

```js
Number.parseFloat(string);
```

- **Example**

```js
Number.parseFloat("432faf"); // 432
Number.parseFloat(" 52f"); // 52
Number.parseFloat("f4432f"); // NaN
Number.parseFloat([5, 4, 4, 3]); // 5
```

> There is also global `parseFloat()` method which has same functionality as `Number.parseFloat()`.

#### Number.parseInt()

- parses a string argument & returns an integer of the **specified radix/base(`2` to `36`)**.
- If `radix` is smaller than `2` or greater than `36` then `NaN` is returned.
- **Syntax**

```js
Number.parseInt(string);
Number.parseInt(string, radix);
```

## Instance Methods

#### Number.prototype.toExponential(fractionDigits)

- It returns a string representing `Number` object in exponential notation.
- Optionally It takes an argument `fractionDigits` which specifies the number of digits after the decimal point. Default value is as many digits as necessary to specify the number.
- If `fractionDigits` is not in range `0` to `100` then `RangeError` is raised.
- **Syntax**

```js
toExponential();
toExponential(fractionDigits);
```

#### Number.prototype.toFixed()

- It formats a number using fixed-point notation and returns formatted number as string.
- Optionally, it takes an argument `digits` which is number of digits to appear after the decimal point(a value between `0` & `20`).
- By default, value of `digits` is `0` if not passed.
- **Syntax**

```js
toFixed();
toFixed(digits);
```

- Possible **exceptions** are `RangeError` & `TypeError`.

#### Number.prototype.valueOf()

- It returns the wrapped primitive value of a `Number` object.
- **Example**

```js
let numObj = new Number(145);
typeof numObj; // object

typeof numObj.valueOf(); // number
```

#### Number.prototype.toString(radix)

- It returns a string representing the specified `Number` object.
- Optionally, It takes an argument `radix` which is in range `2` through `36` and it specifies the base to use for representing numeric values.
- **Example**

```js
const numObj = new Number(234);
numObj.toString(16); // ea
```

- It raises `RangeError` when `radix` is not in range.

#### Number.prototype.toPrecision()

- It returns a string representing the `Number` object to the specified precision.
- `precision` is in range `0` to `100`.
- **Syntax**

```js
toPrecision();
toPrecision(precision);
```

- `RangeError` is raised if `precision` is not in the given range.
- **Example**

```js
const num = 123.434;

num.toPrecision(); // 123.434
num.toPrecision(5); // 123.43
num.toPrecision(4); // 123.4
num.toPrecision(3); // 123
```

#### Number.prototype.toLocaleString()

- **Syntax**

```js
toLocaleString();
toLocaleString(locales);
toLocaleString(locales, options);
```

> `Infinity` & `-Infinity` both are of type **number**.
