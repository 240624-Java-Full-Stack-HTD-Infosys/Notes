# Cumulative for the  1 Way Data Binding
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define One way binding.
</details>
<details><summary>Description</summary>

# Description
Data binding is the idea of connecting UI and state. Angular components are made of several parts, including the template (which we will call the "view" here) and the component class which may contain state (which we will refer to as the "model" for now). When we put the view and the model together we get a model-view. In Angular this is accomplished with data binding. 

## One-Way Data Binding
There are several one-way data binding techniques in Angular which can be mixed together to create two-way data binding.

### String Interpolation
The simpliest one-way binding technique allows us to render data on-screen with string interpolation. To preform string interpolation we use double-curly-brace syntax in the tempalte like so:

```typescript
Hello {{firstName}} {{lastName}}! //will show "Hello Kyle Plummer!"
```

This binds two pieces of state, `firstName` & `lastName`, from the model into the view, showing them on screen. This state would need to exist in, or be available to, the component class. Within the double-curly-braces any valid typescript expression will work.

```typescript
2 + 2 = {{2 + 2}}. //will show "2 + 2 = 4."
```

### Property Binding
The second technique is property binding, where we assign some piece of state to an HTML attribute (or "property"). For instance, if we had an image tag in our HTML and wanted to set the `src` attribute to a URL string we have stored in the component class, we use property binding with square bracket syntax:

```typescript
<img [src]="imageURL">
```

This would bind the value stored in the variable `imageURL` to the `src` property of the HTML element. When an `img` element is rendered, the browser uses this property to find the image data. Whatever string is assigned to `imageURL` is where the browser would look. If a new value is assigned to the `imageURL` variable, Angular would detect the change, get the new image data from the new source, and re-render the component.

### Event Binding
The previous techniques could be thought of as "back to front", in that they are both techniques that bind state to the UI, giving the user some sort of visual information based on the state in the component class. The last one-way binding technique can be thought of as "front to back", it binds actions taken on the view to behaviors defined in the component class. This is event binding. 

With event binding we define some sort of action or event which is detected by an element, triggering some method in the component class. For instance, perhaps we want a button that will increment the value of some state when clicked.

```typescript
@Component({
  selector: 'app-child',
  standalone: true,
  imports: [],
  templateUrl: './child.component.html',
  styleUrl: './child.component.css'
})
export class ChildComponent {
  num: number = 0;

  increment() {
    this.num++;
  }
}
```
Here we have our component class, which contains an `increment()` method. When called, this method increases the local variable `num` by 1. Now we need a button in the template to click:

```HTML
<button (click)="increment()">Click me!</button>
```
Note the `(click)` property is surounded in parentheses. We might call this a synthetic event, though this term is not used in the Angular documentation (it's actually a [React term](https://legacy.reactjs.org/docs/events.html)). There is a corresponding Angular synthetic event for most HTML/JS events we might be familiar with, as well as many more. 
</details>
<details><summary>Summary</summary> 

# Summary

- Binding is communication or link between Template and Model.
- Text interpolation, property binding, event binding and two-way binding are used in Angular. 
- Text Interpolation and property binding transfer data from TypeScript(model) to HTML (Template).
- Event binding transfers data from HTML (Template) to TypeScript (Model).
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
