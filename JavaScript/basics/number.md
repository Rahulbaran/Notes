# [Number]()

- In **JavaScript**, numbers are considered as _floating-point value_ (not an integer).
- numbers can be expressed as _a literal_ or _an object_ using `Number` constructor.
- `Number()` function can be used to convert values of other type to numbers (if can't be converted then `NaN` is returned).

## Constructor

#### Number()

- Creates a new `Number` value.

## Static Properties

#### Number.EPSILON

- It represents the difference between 1 & the smallest floating point number greater than 1.

#### Number.MAX_SAFE_INTEGER

- Represents the maximum safe integer in JavaScript(`2^53 - 1`).
- **Value** - `9007199254740991`

#### Number.MAX_VALUE

- The maximum numeric value representable in JavaScript.
- **Value** - `1.7976931348623157e+308`

#### Number.MIN_SAFE_INTEGER

- Represents the minimum safe integer in JavaScript(`-2^53 - 1`).
- **Value** - `-9007199254740991`

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
- _Type Conversion_ is done (whenever required) before checking for `NaN`.
  > Global `isNaN()` has same functionality as `Number.isNaN()`.

#### Number.isFinite()

- Checks whether the passed value is a finite number.
  > Global `isFinite()` has same functionality as `Number.isFinite()`.

#### Number.isInteger()

- Checks whether the passed value is an integer & returns a boolean value.

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

- parses a string argument & returns an integer of the **specified radix/base**.
