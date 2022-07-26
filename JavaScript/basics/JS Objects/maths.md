# [Math Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math)

- A built-in object that has properties & methods to deal with mathematical functions & constants (It is not a function object).

> `Math` works with `Number` type only (Does not work with `BigInt`).

- Unlike other global objects, `Math` is **not a constructor**. All properties & methods of `Math` are static.

## Static Properties

- Also known as Constants.

#### `Math.E`

- Euler's constant(Epsilon) (base of **natural log**). It's value is approximately `2.718`.

#### `Math.LN2`

- Natural logarithm of `2` (approximately `0.693`)

#### `Math.LN10`

- Natural logarithm of `10` (approximately `2.303`)

#### `Math.LOG2E`

- Base-2 logarithm of `E` (approx `1.443`).

#### `Math.LOG10E`

- Base-10 logarithm of `E`(Epsilon). It's approximately `0.434`.

#### `Math.PI`

- It is the ratio of a circle's circumference to its diameter (approximately `3.14159`).

#### `Math.SQRT1_2`

- Square root of `1/2`. It is approximately `.707`.

#### `Math.SQRT2`

- Square root of `2`. It is apporximately `1.414`.

## Static Methods

#### `Math.abs(x)`

It returns the absolute value of `x`, which means positive value of `x` if it is an integer.

- If `x` is not a integer then `NaN` is returned.

```js
Math.abs(10 - 20); // 10
```

#### `Math.cos(x)`

#### `Math.cosh(x)`

#### `Math.acos(x)`

- It returns the **arccosine** of `x`number (in radians) if `x` is between `-1` & `1` otherwise `NaN`.

- **Example**

```js
Math.acos(1); // 0
Math.acos(2); // NaN
Math.acos(0.5); // 1.0472
```

#### `Math.acosh(x)`

- It returns the **hyperbolic arc-cosine** of number `x`. If `x`is less than 1 or of other type then`NaN` is returned.

- **Example**

```js
Math.acosh(1); // 0
Math.acosh(0.6); // NaN
Math.acosh("Rahul Kumar"); // NaN
Math.acosh(1.2); // 0.6224
```

#### `Math.sin(x)`

#### `Math.sinh(x)`

#### `Math.asin(x)`

- It returns the **arcsine** of number `x`if it is between `-1` & `1` otherwise `NaN`.

- A numeric value between `-π/2` & `π/2` is returned.
- **Example**

```js
Math.asin(-1); // -1.571
Math.asin(1); // 1.571
Math.asin(3); // NaN
Math.asin("Math"); // NaN
```

#### `Math.asinh(x)`

- It returns the **hyperbolic arcsine** of number `x`, otherwise `NaN`.

- **Example**

```js
Math.asinh(); // NaN
Math.asinh("Math"); // NaN
Math.asinh(1); // .8814
Math.asinh(0); // 0
```

#### `Math.tan(x)`

#### `Math.tanh(x)`

#### `Math.atan(x)`

- It returns the **arctangent** of number `x`(in radians) otherwise`NaN`.

- **Example**

```js
Math.atan(1); // .7854
Math.atan(); // NaN
Math.atan(14); // 1.4995
Math.atan("Math"); // NaN
```

#### `Math.atanh(x)`

- It returns the **hyperbolic arctangent** of number `x`otherwise`NaN`.
- `x` should be either greater than `-1` or less than `1`.
- **Example**

```js
Math.atanh(1); // Infinity
Math.atanh(0.9); // 1.472
Math.atanh(); // NaN
Math.atanh(2); // NaN
Math.atanh(0); // 0
```

#### `Math.atan2(y, x)`

#### `Math.cbrt(x)`

- It returns the cube root of a number.

- **Example**

```js
Math.cbrt(NaN); // NaN
Math.cbrt(); // NaN
Math.cbrt(8); // 2
Math.cbrt(9); //  2.08
Math.cbrt(-27); // -3
Math.cbrt(null); // 0
```

#### `Math.sqrt(x)`

#### `Math.hypot(x1, x2,....)`

#### `Math.exp(x)`

#### `Math.expm1(x)`

#### `Math.log(x)`

#### `Math.log10(x)`

#### `Math.log1p(x)`

#### `Math.log2(x)`

#### `Math.ceil(x)`

#### `Math.floor(x)`

#### `Math.trunc()`

> For Positive numbers, `Math.trunc()` & `Math.floor()` do the same thing whereas for Negative Numbers, `Math.trunc()` & `Math.ceil()` do the same thing.

#### `Math.fround(x)`

#### `Math.round(x)`

#### `Math.random()`

#### `Math.pow(x, y)`

#### `Math.max(x1, x2,...)`

#### `Math.min(x1,x2,...)`

#### `Math.sign(x)`
