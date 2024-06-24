# Cumulative for the  Jasmine
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The Basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To describe Jasmine
</details>
<details><summary>Description</summary>

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
</details>
<details><summary>Real World Application</summary>

# Real World Application

- Every Angular compoennet has some functions. Consider a function that is used to display a welcome message "Welocme Username" , the user name is taken from the backend and this function can be tested using jasmine.
- Not just the above function any function, in Angular can be tested using jasmine by using the suites and specs.
</details>
<details><summary>Implementation</summary> 

# Implementation

1. A function that displayes a welcome message.

welcome.ts

```ts
export function welcomeMessage(name: string){

    return "Welcome "+ name;

}
```

welcome.spec.ts

<i><b>Note:</b> every testing file has an extention spec.ts"</i>

```ts
import { welcomeMessage } from "./welcome";

describe('welcome', ()=>{
    it('should return welcome username',()=>{

        const result= welcomeMessage("Sheldon Cooper");
        expect(result).toContain("Sheldon Cooper");

    })
})
```

- `expect()` is used to the assert the result
- `toContain()` is used to check is a particular string is present in the returned string


karma debug:

![Welcome](/modules_new/resources/welcome.png)


2. A function compute that returns 0 if number is negative and increment of number if its positive.

compute.ts

```ts
export function compute(number: number){

    if(number <0){
        return 0;
    }
    else{
        return number +1;
    }

}
```

compute.spec.ts

```ts
import { compute } from "./compute";

describe('compute',() => {
    it('should return zero if number is negative',()=>{

        const result  = compute(-1);
        expect(result).toBe(0);

    })
    it('should return incremnt of number if number is positive',() =>{
        const result = compute(2);
        expect(result).toBe(3);

    })

})
```

- `toBe()` internally uses JavaScript `===`.
- It is used to match the actual and expected values.
- But `toBe()` fails where objects are not identical.
- To check deep equlity `toEqual()` is used.
- There is no difference between the two when comparing primitives. But for objects, `toEqual()` will compare by key/values-content, `toBe()` will compare by object reference.


karma debug:

![compute](/modules_new/resources/compute.png)
</details>
<details><summary>Summary</summary> 

# Summary

- Jasmine is a JavaScript framework that is used to perform unit and intergration tests in Angular.
- A `.spec.ts` file is created for unit testing.
- Each jasmine testing file contains one or more suites with one or more specifications.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
