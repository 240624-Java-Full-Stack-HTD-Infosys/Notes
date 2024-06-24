# Description

### Event Emitters in Angular

An [EventEmitter](https://angular.io/api/core/EventEmitter) is used to emit custom events synchronously or asynchronously, and register handlers for those events by subscribing to an instance.

###  `@Output`  with Event Emmiter

To emit data and events out from a component, we create an instance of EventEmitter and annotate that property with the `@Output` decorator. This instance calls the `emit()` method to emit a payload which can be received by an event object `$event`.