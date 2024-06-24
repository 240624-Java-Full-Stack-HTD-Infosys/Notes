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