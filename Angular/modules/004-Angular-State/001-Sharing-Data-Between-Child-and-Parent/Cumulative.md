# Cumulative for the  Sharing Data Between Child and Parent
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To explain data sharing between parent and child components.
</details>
<details><summary>Description</summary>

# Description
Angular uses `@Input` and `@Output` decorators to share data between components. We can also use Angular services to share data between components. 

If we have to pass data from parent to child, we use the `@Input` decorator. To pass data from child up to parent, we emit the data using the `@Output` decorator with the `EventEmitter` API.

![Component Interaction](/modules/resources/component-interaction.PNG)

### `@Input` decorator

In Angular, the [`@Input`](https://angular.io/api/core/Input) decorator is defined in the [@angular/core](https://angular.io/api/core) package that marks a class field as an **input property** and supplies configuration metadata.

![Input flow](/modules/resources/input-flow.PNG)

### Component events with EventEmitter and `@Output`

In Angular, a component can emit an event using [`@Output`](https://angular.io/api/core/Output) and [EventEmitter](https://angular.io/api/core/EventEmitter) API in the [@angular/core](https://angular.io/api/core) package.

`@Output` decorator that marks a class field as an **output property** and supplies configuration metadata.

![Output Flow](/modules/resources/output-flow.PNG)

### Event Emitters in Angular

An [EventEmitter](https://angular.io/api/core/EventEmitter) is used to emit custom events synchronously or asynchronously, and register handlers for those events by subscribing to an instance.


</details>
<details><summary>Real World Application</summary>

# Real World Application

Any Angular application comprises many components and data transfer between the components is an important aspect of a smooth and functional application.

- Consider an e-commerce website, The app component is a parent component for product and cart component.
- When a product is added to cart the data is tranfered from the product to app component and to the cart component.
</details>
<details><summary>Implementation</summary> 

# Implementation

### `@Input`:

Let us create an angular application with at least one child component. 
- Run the `ng new event-emitter-demo` CLI command to create an Angular application. Here, we already have an AppComponent considered as a parent component.
- Run the `ng g component child` CLI command to create a child component for the AppComponent.

![Child Component](/modules_new/resources/child-component.PNG)

In `child.component.ts`, we create a `count` property and decorate it with the `@Input()`, which implies that the value of the `count` property will be set outside of the ChildComponent.

```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `
    <p> Data from the AppComponent --- count = {{count}}</p>
  `
})
export class ChildComponent {
  @Input() count: number;
}
```

In `app.component.ts`, we use **property binding** to pass the `count` property value from the AppComponent to the ChildComponent.

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <h2>@Input Example</h2>
    <app-child [count]='count'></app-child>
  `
})
export class AppComponent {
  count = 9;
}
```

When we run this application, we can see the below output:

![output screen](/modules_new/resources/input-example.PNG)

</details>
<details><summary>Summary</summary> 

# Summary

- To achieve data flow between child and parent components Angular uses `@Input` and `@Output`.
- `@Input()` lets the parent component update data in the child component.
- `@Output` lets the child component send data to the parent component.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
