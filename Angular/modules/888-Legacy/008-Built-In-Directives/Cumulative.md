# Cumulative for the  Built In Directives
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Angular built-in directives.
</details>
<details><summary>Description</summary>

# Description

**Directive**
- TypeScript classes that add additional behaviour to elements in Angular applications are called Directives.

Different types of Angular directives

1. Component Directives: It is the main class with `@Component` decorator and it contains details like component processing, instantiation and usage at run time.
2. Attribute Directives: directives that listen to and modify the behaviour of other HTML elements, attributes, properties, and components.
3. Structural Directives: Structural directives manipulate DOM elements, these directives start with “*”.  For example `*ngIf` and `*ngFor`.

- Some directives are predefined in Angular, these directives are called built-in directives.

Most common examples for built-in attribute directives:

- `ngClass`: used to add and remove a set of CSS classes.
- `ngStyle` : used to add and remove a set of HTML styles.
- `ngModel`: used to add two-way data binding to an HTML form element.

Most common examples of built-in structural directives:

- `ngIf`: used to conditionally create or dispose of subviews from the template.
- `ngFor`: used to repeat a node for each item in a list.
- `ngSwitch`: used for a set of directives that switch among the alternative views.




</details>
<details><summary>Real World Application</summary>

# Real World Application

- Angular built-in directives can be used to manage forms, lists, styles, and what users see.


</details>
<details><summary>Implementation</summary> 

# Implementation

**Built-in Attribute directives**

1. `ngClass`

A text and buttons to dynamically change the background color based on the button clicked.

app.component.html:

```html
<H2 class="tags">Built-In Attribute Directive ngClass</H2>
<p class="tags" [ngClass]="{ 'orange' : color === 'orange',
'green' : color ==='green',
'blue' : color ==='blue'
}">Click the buttons to change the background color</p>
<div class = "tags">
<button id="orange" class="button" (click)="highlightColor('orange');">Orange</button>
<button id = "green"class ="button"(click)="highlightColor('green');">Green</button>
<button id ="blue" class="button" (click)="highlightColor('blue');">Blue</button>
</div>
```

app.component.ts:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: 'app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  color='white';
  title = "Sample";
  highlightColor(newColor: string):void{
    this.color=newColor

  }
}
```

app.component.css:

```css

.orange {
   color: white;
   background-color: orange;
}

.blue{
    color: white;
    background-color: blue;
}

.green{
    color: white;
    background-color: green;
}

h2{
    align-self: centre;

}

.tags {
    margin: auto;
    padding: 10px;
    text-align: center;

  }

.button{
    margin: 10px;
    width: 100px;
    height: 20px;
    
}

#blue{
    color: white;
    background-color: blue;
    border-color: white;
}
#green{
    color: white;
    background-color: green;
    border-color: white;
}

#orange{
    color: white;
    background-color: orange;
    border-color: white;
}
```

HTML page:

![ngClass](/modules_new/resources/ngClass1.png)

After clicking orange:

![ngClass](/modules_new/resources/ngClass2.png)

After clicking green:

![ngClass](/modules_new/resources/ngClass3.png)

After clicking blue:

![ngClass](/modules_new/resources/ngClass4.png)




</details>
<details><summary>Summary</summary> 

# Summary

Directives are TypeScript classes that add additional features to the Angular application

- Directives are classified into components, structural directives and attribute directives.
- Angular has some built in directives like `ngClass`, `ngStyle`, `ngModel`, `ngIf`, `ngFor` and `ngSwitch` etc.

</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
