# Cumulative for the  Testing in Angular with Jasmine and Karma
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The Basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To explain testing in Angular with Jasmine and Karma.
</details>
<details><summary>Description</summary>

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
</details>
<details><summary>Real World Application</summary>

# Real-World Application

- Every angular component has some functions. Consider a product component. Increment and decrement are two functions to increase and decrease the count of products added to the cart.
- These two functions can be tested using Karma and Jasmine.
</details>
<details><summary>Implementation</summary> 

# Implementation


Consider a component named product. Product has two functions, increment and decrement to increase and decrease the total count of the product.

product.component.ts:

```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-product',
  templateUrl: './product.component.html',
  styleUrls: ['./product.component.css']
})
export class ProductComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

  totalCount = 0;

  increment(){
    this.totalCount+=1;
  }
  decrement (){
    this.totalCount-=1;
  }
}
```
A unit test is created for the product component.
<br>
The following statements are part of every unit test:

1. Arrange
2. Act
3. Assert


- Two tests are created in product.spec.ts to test increment() and decrement().
- Arrange: The ProductComponent is initialized in `beforeEach()`.
- Act: The function corresponding to the test is executed.
- Assert: The value of totalCount is checked.


product.component.spec.ts:

```ts
import { ComponentFixture, TestBed } from '@angular/core/testing';

import { ProductComponent } from './product.component';

describe('ProductComponent', () => {
  let component: ProductComponent;
  let fixture: ComponentFixture<ProductComponent>;

  beforeEach(async () => {

    //Arrange
    component= new ProductComponent;
    await TestBed.configureTestingModule({
      declarations: [ ProductComponent ]
    })
    .compileComponents();

    fixture = TestBed.createComponent(ProductComponent);
    component = fixture.componentInstance;
    fixture.detectChanges();
  });

  it('should create', () => {
    expect(component).toBeTruthy();
  });

  it("should increase totalCount by 1 when incremented",()=>{
    //Act
    component.increment();
    //Assert
    expect(component.totalCount).toBe(1);
  });
  it("should decrease totalCount by 1 when decremented",()=>{
    //Act
    component.decrement();
    //Assert
    expect(component.totalCount).toBe(-1);
  });
});
```

- Run `ng test`.


Karma:

![Karma](/modules_new/resources/AngularTesting1.png)

Karma debug runner:

![Karma Debug](/modules_new/resources/AngularTesting2.png)

- A small change is made in `product.component.spec.ts`. The assert statement for increment method is modified to "0" instead of "1".
- As soon as the changes are saved, Karma runs all the tests again.
- The increment test fails.

Command line output:

![Command Line](/modules_new/resources/AngularTesting3.png)

Karma debug runner:

![Karma Debug](/modules_new/resources/AngularTesting4.png)
</details>
<details><summary>Summary</summary> 

# Summary

- In Angular Karma is the test runner and Jasmine is the testing framework.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
