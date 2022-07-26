# BigInt

- Primitive Data Type
- It is a `primitive wrapper object` which is used for representing & manipulating those values which are **too large** to be represented by `number primitve` (`primitive Bigint` values).
- Only integers can be converted into `Bigint` values.
- It can be created either by calling `BigInt()` or appending `n` at the end of an integer.
- **Example**

```js
const bigIntNum = 453n;
const generalNumber = 4234324324;
const bigIntN = BigInt(generalNumber); // 4234324324n
```

- BigInt values can't be used with methods in the built-in `Math` object & can't be mixed with a Number value in operations.
- `typeof` a BigInt value will be `"bigint"`.
- We can also wrap a BigInt value in an `Object`.

```js
const big = 124n;
typeof Object(big) === "object"; // true
```

### Comparisons

- A BigInt value is not strictly equal to a Number value, but it is loosely so.

```js
0n === 0; // false
2n == 2; // true
```

- We can also compare a Number value & a BigInt value.

```js
2n > 2; // false
2n < 2; // false
2n > 1; // true
2n >= 2; // true
```

- We can also sort an array containing both Number values & BigInt values.

```js
const mixedArray = [5, 3n, 1n, 0, 0n, 2n, 2, 10, -2, -1n];
// Default Sort - [-1n, -2, 0, 0n, 1n, 10, 2n, 2, 3n, 5]
mixedArray.sort();

// It will raise TypeError since subtraction with mixed types isn't possible
mixedArray.sort((a, b) => a - b);

mixedArray.sort((a, b) => (a < b ? -1 : a > b ? 1 : 0)); // [-2, -1n, 0, 0n, 1n, 2n, 2, 3n, 5, 10]
```

### Operators

- `+ * - % **` are the only operators which can be used with BigInt values or object-wrapped BigInt values.

> `/` works with BigInt as expected when whole numbers whereas with fractional result will be truncated.
