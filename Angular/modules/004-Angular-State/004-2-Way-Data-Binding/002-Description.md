# Two-Way Data Binding
We can combine one-way binding techniques to establish two-way binding. For instance, we can have some piece of state be rendered on-screen with string interpolation, and we can set the value of that state based on the value typed into an input field using event binding.

### String Interpolation & Event Binding
Here's the template:
```HTML
<h1>Number: {{num}}</h1>
<br>
<input type="number" (input)="updateNum($event)">
```

And here's the component class:
```typescript
@Component({
  selector: 'app-my',
  standalone: true,
  imports: [],
  templateUrl: './my.component.html',
  styleUrl: './my.component.css'
})
export class MyComponent {
  num: number = 0;

  updateNum(event: any) {
    this.num = event.target.value;
  }
}
```
Whenever we type into the input text box an event is triggered which changes the value of `num`. When `num` changes, Angular detects this and re-renders the component with the new value.

**Note: The combination of string interpolation and event binding is not what the Angular docs call "two-way binding".**

### Property Binding & Event Binding
This next example is a little more complicated. **This is the two-way data binding pattern described by the [Angular docs](https://angular.io/guide/two-way-binding).** 

Recall that components can take inputs and emit outputs using the `@Input()` and `@Output()` decorators. A component which uses these decorators and conforms to a specific pattern can mix property and event binding to form two-way binding. The pattern is this: The input property has name "x", and the output property must be "xChange". If the input property is "size" then the output property must be "sizeChange". If this pattern is kept, we can use "banana-in-a-box" syntax `[()]` for two-way binding.

Here is an example of this in action. We need to consider 4 files, the template and component class for each of two components, parent and child. In this example we will have an input text box tied to the color property of an element, so that when we type a color into the text box the color of the element will change to match.

#### Parent
Template - `parent.component.html`:
```html
<app-child [(color)]="colorValue"></app-child>
<h1 [style.color]="colorValue">{{colorValue}}</h1>
```
Note the "banana-in-a-box" syntax here: `[(color)]`. Color is a property of the child component. This is the two-way binding.

Component Class - `parent.component.ts`:
```typescript
@Component({
  selector: 'app-parent',
  standalone: true,
  imports: [ChildComponent],
  templateUrl: './parent.component.html',
  styleUrl: './parent.component.css'
})
export class ParentComponent {
  colorValue: string = "Color Me!";
}
```
Here we have `colorValue` which is the piece of state that holds our color. 

#### Child
Template - `child.component.html`:
```html
<input type="text" (input)="updateValue($event)">
```
This event binding here causes an `input` event with each character we type into the text box.

Component Class - `child.component.ts`:
```typescript
@Component({
  selector: 'app-child',
  standalone: true,
  imports: [],
  templateUrl: './child.component.html',
  styleUrl: './child.component.css'
})
export class ChildComponent {
  @Input() color!: string;
  @Output() colorChange = new EventEmitter<string>();

  updateValue(event: any) {
    this.colorChange.emit(event.target.value);
  }
}
```
Here we have that pattern, input property `color` and output emitter `colorChange`. Note that `color` is of the same type that the `EventEmitter` wraps, `string`.

Whenever we type into the child component's text box an event is triggered which emits the text we typed. That text is sent to the `color` property of the `<app-child>` element. When a valid color is typed, you will see the color of the text change. 



### ngModel
Because HTML elements do not conform to the x/xChange pattern described above, there is a special tool to establish two-way binding (property & event binding) on form fields. 

`ngModel` is a directive that is part of the Angular `FormsModule`. In order to use the directive, you must import the `FormsModule` class in the component class file, and add it to the `imports` array.

Here is our component class file:

```typescript
import { Component } from '@angular/core';
import { FormsModule } from '@angular/forms';

@Component({
  selector: 'app-my-component',
  standalone: true,
  imports: [FormsModule],
  templateUrl: './my-component.component.html',
  styleUrl: './my-component.component.css'
})
export class MyComponentComponent {
  state: string = "initial state";

  reset() {
    this.state = "initial state";
  }
}
```

And here's the template:

```HTML
<h1>{{state}}</h1>
<input type="text" [(ngModel)]="state">
<button (click)="reset()">reset</button>
```

Our input element here is bound to the `state` variable thanks to `ngModel`. If we type into that text box, the value of `state` changes. If we click the button to reset it back to its initial value, the text in the box reverts as well.

### 2-Way Binding with Signals
Lastly, a new feature was introduced with version 17, making 2-way binding even easier with signals. We don't need to worry about `@Input()` or `@Output()` properties, all we need is the `model()` funciton.

#### Parent
Template - `parent.component.html`:
```html
<h1>Parent value: {{parentValue}}</h1>
<hr>
<app-child [(childValue)]="parentValue"></app-child>
```
Here we have the "banana-in-a-box" syntax. `childValue` is a data-bound property of the child element. It is bound to the parent's `parentValue`.

Component Class - `parent.component.ts`:
```typescript
@Component({
  selector: 'app-parent',
  standalone: true,
  imports: [ChildComponent],
  templateUrl: './parent.component.html',
  styleUrl: './parent.component.css'
})
export class ParentComponent {
  parentValue = 101;
}
```
Note the starting value of `parentValue` is 101. When the child component is constructed this value is "sent down" and used by the child as an input.

#### Child
Template - `child.component.html`:
```html
<h1>Child value: {{childValue()}}</h1>
<button (click)="increment()"><h3> + + </h3></button>
<button (click)="decrement()"><h3> - - </h3></button>
```
We have two buttons here for incrementing and decrementing the value within the child component.

Component Class - `child.component.ts`:
```typescript
@Component({
  selector: 'app-child',
  standalone: true,
  imports: [],
  templateUrl: './child.component.html',
  styleUrl: './child.component.css'
})
export class ChildComponent {
  childValue = model(0);

  increment() {
    this.childValue.update((val) => {return ++val;});
  }

  decrement() {
    this.childValue.update((val) => {return --val;});
  }
}
```
Note the way we modify the value of `childValue` here. Just like updating any other signal, we use the `update()` function and pass a callback function which tells Angular how to modify `childValue`.

Similar to the way we initialize a writable signal, here we initialize with `model()` and pass an initial value which also sets the data type for this signal. Recall that we passed the initial value 101 in from the parent, the value of 0 will never be shown.