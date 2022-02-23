#### Automated Testing

- It is a way of testing code with less human intervention.
- It helps you keep your test files separated from your actual code.
- Output is easy to read and understand.
- Guarantees code works as expected.
- Instantly see if anything has broken when making changes.

### Testing Methodology (approach)

1. **TDD (Test Driven Development)** - We write automated scripts for testing
2. **BDD (Behavior Driven Development)** - We write whatever we are expecting from the application (in simple english) before writing any code.

- In **BDD** approach, we take the following steps:-

  1. Write our expectation(plan) in plain english
  2. Write automated scripts for testing
  3. Write easiest code which passes the test
  4. Refactor the codes to make it more optimized.
  5. Repeat the same approach(1-4) for furthur testing

- In **BDD**, we follow **Red > Green > Refactor** approach.

- Both of these methodology force us to write automated tests first and code second.

### Testing Types

- Unit Testing
- Integration Testing
- End To End Testing

### Some Testing Frameworks

- **chai** - For Assertion Part of testing (Can be used for TDD & BDD Both). It is an expectation library.

- **mocha** - For getting a summary (informative summary) about a failing test. (Test Sweet has been introduced to define a group of tests)

- **jest**
- **jasmine**
- **cucumber**
- **cypress**

##### mocha

- We call all our test files in a directory called **test** in the root and write a script in **package.json** to run `mocha`.
