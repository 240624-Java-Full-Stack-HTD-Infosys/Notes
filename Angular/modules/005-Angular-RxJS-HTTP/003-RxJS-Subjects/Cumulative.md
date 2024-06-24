# Cumulative for the  RxJS Subjects
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The Basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define RxJS Subjects.


</details>
<details><summary>Description</summary>

# Description

A  RxJS Subject is special type of Observable that multicasts to many Observers.

- Every Subject is an Observable. A Subject can be subscribed providing an Observer. From the perspective of the Observer, it is ambigious to tell of the Observable execution is coming from Observable or a Subject.
- Every Subject is an Observer. It is an object with methods `next(v)`, `error(e)` and `complete()`. `next(theValue)` can be used to feed a value to the subject and it will be multicasted to the Observers registered to listen to the Subject.
</details>
<details><summary>Real World Application</summary>

# Real-World Application

- Since a Subject is an Observable, Consider a scenario where a selector is created for employee id.When you now subscribe to this selector / observable, everytime the employee id state changes, your observable emits the new employee id. using this you can bind html template variables to these observable which would update your employee id in your page automatically.
</details>
<details><summary>Implementation</summary> 

# Implementation

Implementation of Subject as an Observable

```ts
import { Subject } from 'rxjs';

const subject = new Subject<number>();

subject.subscribe({
  next: (v) => console.log(`observerA: ${v}`),
});
subject.subscribe({
  next: (v) => console.log(`observerB: ${v}`),
});

subject.next(1);
subject.next(2);

```

Console output:

```console
observerA: 1
observerB: 1
observerA: 2
observerB: 2
```

Implementation of Subject as an Observer

```ts
import { Subject, from } from 'rxjs';

const subject = new Subject<number>();

subject.subscribe({
  next: (v) => console.log(`observerA: ${v}`),
});
subject.subscribe({
  next: (v) => console.log(`observerB: ${v}`),
});

const observable = from([1, 2, 3]);

observable.subscribe(subject); 
```

Console log:

```console
observerA: 1
observerB: 1
observerA: 2
observerB: 2
observerA: 3
observerB: 3
```
</details>
<details><summary>Summary</summary> 

# Summary

- RxJS Subject is an Observable that can be multicasted to many Observers.
- RxJS Subject acts as both an Observer and Observable.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
