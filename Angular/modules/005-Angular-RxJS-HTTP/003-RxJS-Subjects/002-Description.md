# Description

A  RxJS Subject is special type of Observable that multicasts to many Observers.

- Every Subject is an Observable. A Subject can be subscribed providing an Observer. From the perspective of the Observer, it is ambigious to tell of the Observable execution is coming from Observable or a Subject.
- Every Subject is an Observer. It is an object with methods `next(v)`, `error(e)` and `complete()`. `next(theValue)` can be used to feed a value to the subject and it will be multicasted to the Observers registered to listen to the Subject.