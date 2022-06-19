## ternary operator

- Only JS operator which taks 3 operands.
- Syntax :-

```bash
    <condition> ? <expIfTrue> : <expIfFalse>;
```

## Increment Operator (++)

- It increments (adds one to) its operand & returns a value.
- If **postfix** is used (`++` after operand ---> `x++`) then the operand is incremented & value(operand) is returned before incrementing.
- If **prefix** is used (`++` before operand ---> `++x` ) then the operand is incremented & value(operand) is returned after incrementing.
- **Example**

```js
// Postfix Increment
let a = 10;
let b = a++; // a = 11, b = 10

// Prefix Increment
let x = 15;
let y = ++x; // x = 16, y = 16
```

## Decrement Operator (--)

- It decrements (subtracts one from) its operand & returns a value.
- If **postfix** is used (`--` after operand ---> `x--`) then the operand is decremented & value(operand) is returned before decrementing.
- If **prefix** is used (`--` before operand ---> `--x` ) then the operand is decremented & value(operand) is returned after decrementing.
- **Example**

```js
// Postfix Decrement
let a = 10;
let b = a--; // a = 9, b = 10

// Prefix Decrement
let x = 15;
let y = --x; // x = 14, y = 14
```
