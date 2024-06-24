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