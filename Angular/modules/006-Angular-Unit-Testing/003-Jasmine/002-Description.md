# Description

Jasmine is a JavaScript framework that is used to write and execute unit tests and Intergration tests.

Three important parts of jasmine

1. A library with classes and functions for constructing tests.
2. A test execution engine.
3. A reporting engine that outputs test results in different formats

- In jasmine every test consists of one or more suites and each suite consists of one or more specifications.

Suites and specifications are written as:

```js
describe('Suite description', () => {
  it('Spec description', () => {
    /* … */
  });
  /* … more specs …  */
});
```