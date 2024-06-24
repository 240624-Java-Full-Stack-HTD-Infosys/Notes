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