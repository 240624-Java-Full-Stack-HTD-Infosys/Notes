# Description

## Automated Testing

- The practice of writing code to test our code and run those tests in an automated fashion.
- Automated testing is more efficient than manual testing.
- Automated tests are used to catch the defects before releasing the software.

## Types of Testing

### Unit Tests

- Angular components are tested in isolation, without external resources(e.g.file system, database, API endpoints) using unit tests.

- Unit tests are easy to write and super fast.

### Integrated Tests

- Angular components are tested with external resources using integration tests.
- Integrated tests are run on a component with a template and a fake service.

### End To End Tests

- The entire application is tested as a whole using the end-to-end test.
- End-to-end tests are very slow and a even small change can break the entire test.

<i>**Note:** Mostly unit tests and integration tests are preferred as end-to-end tests are time consuming and fragile.</i>

## Testing In Angular

- In Angular, Karma is the test runner and Jasmine is the testing framework.
- Karma checks for `component_name.spec.ts` file to run the tests.
- Jasmine has inbuilt funtions like `describe()` and `it()` to write tests.
