# Implementation

### `@Input`:

Let us create an angular application with at least one child component. 
- Run the `ng new event-emitter-demo` CLI command to create an Angular application. Here, we already have an AppComponent considered as a parent component.
- Run the `ng g component child` CLI command to create a child component for the AppComponent.

![Child Component](/modules_new/resources/child-component.PNG)

In `child.component.ts`, we create a `count` property and decorate it with the `@Input()`, which implies that the value of the `count` property will be set outside of the ChildComponent.

```typescript
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  template: `
    <p> Data from the AppComponent --- count = {{count}}</p>
  `
})
export class ChildComponent {
  @Input() count: number;
}
```

In `app.component.ts`, we use **property binding** to pass the `count` property value from the AppComponent to the ChildComponent.

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <h2>@Input Example</h2>
    <app-child [count]='count'></app-child>
  `
})
export class AppComponent {
  count = 9;
}
```

When we run this application, we can see the below output:

![output screen](/modules_new/resources/input-example.PNG)

