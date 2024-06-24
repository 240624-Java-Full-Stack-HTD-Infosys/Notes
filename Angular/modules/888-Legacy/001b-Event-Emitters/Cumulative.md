# Cumulative for the b Event Emitters
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Event Emmitters
</details>
<details><summary>Description</summary>

# Description

### Event Emitters in Angular

An [EventEmitter](https://angular.io/api/core/EventEmitter) is used to emit custom events synchronously or asynchronously, and register handlers for those events by subscribing to an instance.

###  `@Output`  with Event Emmiter

To emit data and events out from a component, we create an instance of EventEmitter and annotate that property with the `@Output` decorator. This instance calls the `emit()` method to emit a payload which can be received by an event object `$event`.
</details>
<details><summary>Real World Application</summary>

# Real World Application

- In an ecommerce website consider the product list and cart components.
- Whenever a product is added in product list an event emitter productAdded is used to send product details to app component and then to cart.
- When ever a product is removed from the cart an event emitter productRemoved is used to remove product.


</details>
<details><summary>Implementation</summary> 

# Implementation

In `child.component.ts`, we create a `change` property and decorate it with the `@Output()` and bound a new instance of `EventEmitter` to it.

Also, we have two methods - `increment()` and `decrement()` which update the value of the `count` property based on the event (clicking on the increment count/ decrement count buttons) and emits the event changes to its parent component.

Here, the `change` property calls the `emit()` method that emits the `count` value which can be received by the event object `$event`.

```typescript
import { Component, Input, Output, EventEmitter } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `
    <p> Click this button to increment the count: </p>
    <button (click)='increment()'>increment count</button> <br>
    <p> Click this button to decrement the count: </p>
    <button (click)='decrement()'>decrement count</button>
  `
})
export class ChildComponent {
  @Input()
  count: number = 0;

  @Output()
  change: EventEmitter<number> = new EventEmitter<number>();

  increment() {
    this.count++;
    this.change.emit(this.count);
    console.log("incrementing count in the child component....." + this.count + " --- passing to AppComponent");
  }

  decrement() {
    this.count--;
    this.change.emit(this.count);
    console.log("decrementing count in the child component....." + this.count + " --- passing to AppComponent");
  }
}
```

In `app.component.ts`, we use **event binding** to get the `count` property value from the ChildComponent to the AppComponent.

The `.emit()` method emits the changes to our `(change)` event listener we set up in the AppComponent, to which our `countChange($event)` callback will be invoked, and the data associated with the event will be given to us via the `$event` property.

We assign `this.count` with the `event` that’s passed back inside the `countChange()` method.

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <h2>Event Emitters</h2>
    <p> At AppComponent, count = {{ count }} </p>
    <app-child [count]='count' (change)= 'countChange($event)'></app-child>
  `
})
export class AppComponent {
  count = 9;
  countChange(event) {
    this.count = event;
  }
}

```

When we run this application, we can see the below output:

![Event Emitter Output](/modules_new/resources/event-emitter-example.PNG)

In this example, we use property binding to send the `count` value from the parent component to the child component and we use custom event binding to get the updated `count` value from the child component to the parent component.

</details>
<details><summary>Summary</summary> 

# Summary

- Event emitters are used to emit custom events synchronously or asynchronously.
- Event emmiters are used along with `@Output` to transfer data from child to parent.


</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
