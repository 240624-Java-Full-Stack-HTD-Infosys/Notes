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


