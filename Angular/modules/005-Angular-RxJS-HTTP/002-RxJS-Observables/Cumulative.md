# Cumulative for the  RxJS Observables
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The Basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Observer design pattern.
- To define RxJS Observables.


</details>
<details><summary>Description</summary>

# Description

## Observer design pattern

Observer pattern is used to implement one-to-many relationship between objects. If one object is modified, its depenedent objects are notified automatically. Observer pattern falls under behavioral pattern category.

The following image explains the observer pattern.

![Observer Pattern](/modules_new/resources/Observer.PNG)

The two main stratergies in observer pattern are:

1. **Push**: when an even happens the Observable object will send new data to all the Observers and notifies them.
2. **Pull**: when a even happens the Observable object will notify all the observers but unlike push each observer will pull the information it needs from the Observable.

## RxJS Observable

RxJS is the most popular library for Observer design pattern. The data can be:

- **Observable**: An invokable collection of future values or events
- **Observer**:A collection of callbacks thet listens to values delevered by the Observable.
- **Subscription**: Execution of an Observable, also useful for cancelling the execution.
- **Operators**: Functions to perform actions  like map, filter,concat and flatMap etc.
- **Subject**: Simmilar to EventEmmiter, used to multicast a value or event to multiple Observers.
- **Schedulers**: Centralized dispatchers to control concurrency.
</details>
<details><summary>Real World Application</summary>

# Real World Application

- RxJS observables are used for HTTP Requests.
- RxJS observables are used in combination with WebSockets where you get an asynchronous steam of data.
</details>
<details><summary>Implementation</summary> 

# Implementation

The following is the simple implementation of a button when clicked sends a console.log message "Button cliked!".

```ts
const button = document.querySelector('button');
button.addEventListener('click', () => console.log('Button clicked!'));
```

The above code can be implemented using RxJS observable as follows


```ts
var button = document.querySelector('button');
Rx.Observable.fromEvent(button, 'click').subscribe(() => console.log('Button clicked!'));
```

The difference between the two implemntations :

- Rx.Observable.fromEvent(button, ‘click’) is the interface that listens for button click events (Observable).
- A callback function receives notification of the click event and logs Button Clicked! to the console (Observer).
- We call our Observable, passing it the Observer callback (Subscription).

### Methods to create an observable

- Multiple values: 

```ts
const observable = Rx.Observable.of('hello', 'world');
```
- An Array:

```ts
const observable = Rx.Observable.from([1,2,3]);
```
- An event:

```ts
const observable = Rx.Observable.fromEvent(document.querySelector('button'), 'click');
```
- A promise

```ts
const observable = Rx.Observable.fromPromise(fetch('/users'));
```
- A dunction

```ts
const observable = Rx.Observable.create(observer => observer.next('1'));
```

### Subscribing to observables and Executing the Observable

Subscribing is like calling a function.

There are three types of values an Observable Execution can deliver:

- **Next** : sends a value such as a Number, a String, an Object, etc.
**Error**: sends a JavaScript Error or exception.
**Complete**: does not send a value.

```ts
import { Observable } from 'rxjs';

const observable = new Observable((subscriber) => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  setTimeout(() => {
    subscriber.next(4);
    subscriber.complete();
  }, 1000);
});

console.log('just before subscribe');
observable.subscribe({
  next(x) {
    console.log('recieved value ' + x);
  },
  error(err) {
    console.error('an err occurred: ' + err);
  },
  complete() {
    console.log('completed');
  },
});
console.log('just after subscribe');
```

The output of the code is

```console
just before subscribe
recieved value 1
recieved value 2
recieved value 3
just after subscribe
recieved value 4
completed
```

### Disposing Observable

The following code is implemented to dispose an observable.

```ts
const subscription = observable.subscribe((x) => console.log(x));
```


</details>
<details><summary>Summary</summary> 

# Summary

- RxJS is most popular library of Observable design pattern.
- The data is passed from the Observable object to Observer either by pull or push.
- Observable is a collection of data and the Observable is executed by Subscription.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
