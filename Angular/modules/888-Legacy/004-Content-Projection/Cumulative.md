# Cumulative for the  Content Projection
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define content projection.
</details>
<details><summary>Description</summary>

# Description

## Content Projection

Content projection is the process of inserting or projecting the content into the desired component.

### Implementations of contnet projection

1. Single-slot content projection: projecting content to a component from a single source.
2. Multi-slot content projection: projecting content to a component from multiple sources.
3. Conditional content projection: the content projected is rendered only when the conditions are satisfied.

### <ng-content>

`<ng-content>` is a placeholder, used to project the message into the component.

- `<ng-content>`, `<ng-template>` and `<ng-container>` are used for content projection
</details>
<details><summary>Real World Application</summary>

# Real-world application

- Consider a scenario of asking multiple questions to a user based on the different types of inputs.
- This can be achieved by content projection, a component test can be created. It will hold all the questions.
- A question component can be created and reused.
</details>
<details><summary>Implementation</summary> 

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



</details>
<details><summary>Summary</summary> 

# Summary

- Content projection is the process of projecting content to a different component.
- Content projection can be of single slot, muti-slot and conditional.
- `<ng-content>`, `<ng-template>` and `<ng-container>` are used for content projection.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
