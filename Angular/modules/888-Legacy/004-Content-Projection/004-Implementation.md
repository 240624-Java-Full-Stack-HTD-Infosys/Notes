# Implementation

 A new component named content is created by running the below command in the terminal.

 ```properties
 ng generate component content
 ```

### 1. Single line content projection:


The `<ng-content>` acts as a placeholder for the paragarph "It works!".

content.component.ts:

```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-content',
  template:`<h3>Single slot content projection</h3>
  <ng-content></ng-content>`,
  styleUrls: ['./content.component.css']
})
export class ContentComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}
```

app.component.html:

```html
<app-content>
    <p>It works!</p>
</app-content>
```

HTML page:

![Single line content projection](/modules_new/resources/SingleSlot.png)

### 2. Multi slot content projection

- Selector is used to select the specific tag for a `<ngContent>`.
- The first `<ngContent>` is a placeholder for paragraph "Default text".
- The second `<ngContent>` has a selector "question". So, it acts as a placeholder for the paragraph "Is multi-slot content projection working?".

content.component.ts:

```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-content',
  template:`
  <h3>Multi slot content projection</h3>
  Default:
  <ng-content></ng-content>

  Question:
  <ng-content select="[question]"></ng-content>`,
  styleUrls: ['./content.component.css']
})
export class ContentComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}
```

app.component.html

```html
<app-content>
    <p question>Is multi-slot content projection working?</p>
    <p>Default text</p>
</app-content>
```

HTML page:

![Multi-slot content projection](/modules_new/resources/MultiSlot.png)

### 3. Conditional content projection

- `<ng-content>` can not be used in conditional projection because the content is initialized even if `*ngIf` is false.
- `<ng-template>` is used for conditional projection as the content is not rendered until the condition is satisfied.
- Angular will not initialize the content of an `<ng-template>` element until that element is explicitly rendered.
- normally `<ng-template>` is used as elseblock for an `*ngIf` tag.

app.component.html:

```html
<div *ngIf="true" else elseBlock>
    Condition is true
</div>
<ng-template #elseBlock>
<div>Condition is false</div>
</ng-template>
```

app.component.html:

```html
<app-content></app-content>
```

HTML page:

![Conditional Propagation](/modules_new/resources/Conditional.png)



