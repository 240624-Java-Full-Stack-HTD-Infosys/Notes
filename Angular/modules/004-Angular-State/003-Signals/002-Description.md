# Description
Signals are an angular feature to handle and track changing application state in order to optimize rendering updates. A signal is a wrapper around a value which notifies consumers of that state when it changes. There are two types of signals, **writable** and **computed**.

## Writable Signals
Writable signals allow you to set and update the value directly. A writable signal is of type `WritableSignal` and can be created with the `signal()` function. This function returns a getter function that can be used to read the current value.

```typescript
let count: WritableSignal<number> = signal(0);
```
Here we have created a writable signal. Note the type, which is `WritableSignal<number>`. The type parameter `number` is indicating that this `WritableSignal` is a wrapper around a value of the `number` type. We now have a Signal object representing a number with an initial value of 0.

We can read the current value of our signal by simply calling our `count` variable as a function:
```typescript
console.log(`Current value: ${count()}`)
```

Our signal object, `count`, can also be used to call the `set()` and `update()` methods, which will modify the value. `set()` simply takes in a new value, while `count()` takes in a function which describes how to modify the value.

```typescript
count.set(10)
```
Here we change the value to 10.
```typescript
count.update((value: number) => {return ++value;})
```
And here we update the value by incrementing it. Note the function sent to `update()` takes in a single parameter of the same type our signal wraps around, and returns the new value.

## Computed Signals
Computed signals are calculated based on other signals. These are of type `Signal` and are created with the `computed()` funciton. Instead of an initial value, we pass a function which describes how to calculate the value.
```typescript
let square: Signal<number> = computed(() => {
    return count() * count();
});
``` 
Here we have created a computed signal called `square` which is based on the value of `count`. Just like writable signals we can now call `square()` to get the current value. Note that we didn't have to pass `count` as a parameter, we simply use it. This makes `square` dependent on `count`, and whenever `count` updates, `square` will as well.

## Effects
Effects utilize signals to drive behaviors. We create an effect by calling `effect()` and pass a function which describes the behavior. 
```typescript
    effect(() => {
      console.log(`${count()} * ${count()} = ${square()}.`)
    });
```
This effect will log the values of `count` and `square` to the console whenever they are changed. 

## Optimization of Updates
The purpose of signals is to optimize change detection and rendering. When a signal value is changed all consumers of that value are notified. Components which consume signals are automatically re-rendered once the value is updated. 