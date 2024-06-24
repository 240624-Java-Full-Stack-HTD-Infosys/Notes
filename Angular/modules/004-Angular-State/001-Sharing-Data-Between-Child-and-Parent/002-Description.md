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


