# Automated Testing

- It is a way of testing code with less human intervention.
- It helps you keep your test files separated from your actual code.
- Output is easy to read and understand.
- Guarantees code works as expected.
- Instantly see if anything has broken when making changes.

### Testing Methodology (approach)

1. **TDD (Test Driven Development)** - We write automated scripts for testing and then write code.
2. **BDD (Behavior Driven Development)** - We note whatever we are expecting from the application (in simple english) then we write the automated testing scripts & then code.

- In **BDD** approach, we take the following steps:-

  1. Write our expectation(plan) in plain english
  2. Write automated scripts for testing
  3. Write easiest code which passes the test
  4. Refactor the codes to make it more optimized.
  5. Repeat the same approach(1-4) for furthur testing

- In **BDD**, we follow **Red > Green > Refactor** approach.

- Both of these methodology force us to write _automated tests_ first and code second.

### Testing Types

- Unit Testing(UT)
- Integration Testing(IT)
- End To End Testing(ETE)

### Test suite

- A set of **test cases** that are used to test a software program for showing a specified behavior.
- **Test suite** is used to test a particular behavior of a software.
- Also known as **Validation suite**.
- Each unit test is sometimes called a **Test Spec**.

### Some Testing Frameworks

- **chai** - For Assertion Part of testing (Can be used for TDD & BDD Both). It is an expectation library.
- **mocha** - For getting a summary (informative summary) about a failing test. (Test Sweet has been introduced to define a group of tests)
- **jest**
- **jasmine**
- **cucumber**
- **cypress**

#### mocha

- We call all our test files from a directory called **test** in the root and write a script in **package.json** to run `mocha`.
- `describe()` is used to define a **Test Suite**. It takes two arguments:-
  - a string - Describes about the **Test Suite**
  - a callback function - Contains all the **Test Specs**
- Similar to `describe()`, `it()` also takes two arguments:-
  - a string - Describes the behavior of **Test Spec**
  - a callback function - It contains the expectation

#### chai

- `ok` is an assertion method in **chai**. It tests if a value is _truthy_.

#### jest

- Contains features of `chai` & `mocha` both.
- `describe()` is used to create a **test suite** containing related tests.
- `it()` or `test()` is used to create a **test block**.
- `expect()` uses **Matchers** to check for certain conditions. Some Common **Matchers** are:-

  - `.toBe(value)`
  - `.toEqual(value)`
  - `.toStrictEqual(value)`
  - `.toBeFalsy()`
  - `.toBeTruthy()`
  - `.toBeDefined()`
  - `.toBeUndefined()`
  - `.toBeNaN()`
  - `.toBeNull()`
  - `.toBeGreaterThan(number | bigint)`
  - `.toBeGreaterThanOrEqual(number | bigint)`
  - `.toBeLessThan(number | bigint)`
  - `.toBeLessThanOrEqual(number | bigint)`
  - `.toBeCloseTo(number, numDigits?)`
  - `.toMatch(regexp | string)`
  - `.toContain(item)`
  - `.toContainEqual(item)`
  - `.toHaveLength(number)`
  - `.toHaveProperty(keyPath, value?)`
  - `.toBeInstanceOf(Class)`
  - `.toThrow(error?)` or `toThrowError(error?)`

- While using `.toThrow()`, in order to test that any function throws when called, we need to wrap the code in a function, otherwise the error will not be caught and assertion will fail.

- optional argument `error` passed in `toThrow()` can be either of this:-
  - regular expression
  - string
  - error object: error msg is **equal to** the msg property of the object.
  - error class: error object is **instance of** class.

```javascript
const sum = (a, b) => {
  if (typeof a !== "number" || typeof b !== "number") {
    throw new Error("some of the arguments are not of number types");
  } else {
    return a + b;
  }
};

test("sum() for adding two numbers", () => {
  expect(() => sum(1, "5")).toThrow(/\w{1,}/);
});
```
