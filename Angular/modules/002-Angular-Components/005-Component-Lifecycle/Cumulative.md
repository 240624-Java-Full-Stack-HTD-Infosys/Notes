# Cumulative for the  Component Lifecycle
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Angular lifecycle hooks.
</details>
<details><summary>Description</summary>

# Description

- Angular Component Lifecycle is described using the Lifecycle Hooks.

## Components Life Cycle Hooks

Angular creates a component; renders it; creates and renders its children; checks it when its data-bound properties change; and destroys it before removing it from the DOM. These events are called **Lifecycle Hooks**. These Lifecycle hooks have eight different function calls which correspond to the lifecycle event. Every angular component has a life cycle event carried out in 2 different phases -  one linked to the component itself and the other linked to the children of that component.

## Eight lifecycle hooks in Angular

The below diagram illustrates the order in which the eight hooks are executed.

![Lifecycle Hooks](/modules_new/resources/hooks.png)

**constructor()** - The constructor of the component class gets executed first, before the execution of any other lifecycle hook events. If we need to inject any dependencies into the component, then the constructor is the best place to do so.

#### Lifecycle Hooks

**ngOnChanges()** - Called whenever the input properties of the component change. It returns a *SimpleChanges* object which holds any current and previous property values.

**ngOnInit()** - Called once to initialize the component and set the input properties. It initializes the component after Angular first displays the data-bound properties. 

**ngDoCheck()** - Called during all change-detection runs that Angular can't detect on its own. Also called immediately after the `ngOnChanges()` method.

**ngAfterContentInit()** - Invoked once after Angular performs any content projection into the component’s view.

**ngAfterContentChecked()** - Invoked after each time Angular checks for content projected into the component. It's called after `ngAfterContentInit()` and every subsequent `ngDoCheck()`.

**ngAfterViewInit()** - Invoked after Angular initializes the component's views and its child views.

**ngAfterViewChecked()** - Invoked after each time Angular checks for the content projected into the component. a It called after `ngAfterViewInit()` and every subsequent `ngAfterContentChecked()`.

**ngOnDestroy()** - Invoked before Angular destroys the directive or component.


 
</details>
<details><summary>Real World Application</summary>

# Real World Application

- Angular works using a component-based architecture. 
- Initially `constructor()` is called, followed by `ngOnChnages()`, `ngOnInit()`, with every keystroke, `ngDoCheck()` is called, followed by `noAfterContentInit()`, `ngAfterContentChecked()`, `ngAfterViewInit()`, `ngAfterViewChecked()` and finally `ngOnDestroy()`, if the component is destroyed.
</details>
<details><summary>Implementation</summary> 

# Implementation

To implement all the lifecycle hooks, two components parent and child are created using the following commands.

```properties
ng generate component parent
```

```properties
ng generate component child
```

Now add the parent component to the app component and add the child component to the parent component.

app.component.html:

```html
<app-parent></app-parent>
```

parent.component.html

```html
<p><b>Parent works!</b></p>
<app-child></app-child>
```

```html
<p><b>Child works!</b></p>
```

1. `ngOnInit()`: Called after the component is loaded into the DOM.

- The `ngOnInit()` is implemented by OnInit interface.
- A console.log statement is added to `ngOnInit()` in both child and parent components and the `constructor()`.

app.parent.ts

```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html',
  styleUrls: ['./parent.component.css']
})
export class ParentComponent implements OnInit {

  constructor() { 
    console.log("Parent Constructor Called");
  }

  ngOnInit(): void {
    console.log("Parent ngOnInit called");
  }

}


```

app.child.ts

```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit {

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
  }

}

```

HTML page:

![ngOnInit](/modules_new/resources/ngOnInit.PNG)

2. `ngOnDestroy()`: called before the component is removed from the DOM.

- A button is called to invoke and destroy the child component.
- The `ngOnDestroy()` method from OnDestroy interface is implemented in child component.

parent.component.html

```html
<p><b>Parent works!</b></p>
<button (click)="toggleChild();">Child Component</button>
<app-child *ngIf="isChild" ></app-child>
```

parent.component.ts:

```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html',
  styleUrls: ['./parent.component.css']
})
export class ParentComponent implements OnInit {
  isChild = false;

  constructor() { 
    console.log("Parent Constructor Called");
  }

  ngOnInit(): void {
    console.log("Parent ngOnInit called");
  }
  toggleChild(){
    this.isChild=!this.isChild;
  }

}
```

child.component.ts:

```ts
import { Component, OnDestroy, OnInit } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit ,OnDestroy{

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
  }
  ngOnDestroy(): void {
      console.log("Child Component is Destroyed")
  }
  
}
```

HTML page:

![ngOnChangeParent](/modules_new/resources/ngOnChangesParent.PNG)

HTML page after child component is invoked(child component button is clicked):

![ngOnChangeChild](/modules_new/resources/ngOnChangesChild.PNG)

HTML page after child component is Destroyed (child component button is clicked again):

![ngOnDestroyChild](/modules_new/resources/ngOnDestroy.PNG)

3. `ngOnChanges()`: called once before `ngOnInit()` and when a data-bound input changes.

- The `ngOnChanges()` method is implemnted with a console.log statement in child component.
- A text input is created with two-way binding using `ngModel`.
- The text (data) is passed from parent to child component using `@Input` (data bound Input) and displayed using the text Interpolation.

<i> **Note**: FormsModule  should be imported and added to imports in NgModule to use ngModel. </i>

<i> **Note**: The concepts data binding and string interpolation are explained in upcomming modules. </i>

child.component.ts

```ts
import { Component, OnDestroy, OnInit, OnChanges, SimpleChanges, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit ,OnDestroy, OnChanges{

  @Input()
  name ='';

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
  }
  ngOnChanges(changes: SimpleChanges): void {
      console.log("Child ngOnChanges called")
  }
  ngOnDestroy(): void {
      console.log("Child Component is Destroyed")
  }
  

}
```

child.component.html:
```html
<p><b>Child works!</b></p>
<p>{{name}}</p>
```
parent.component.ts
```ts
import { Component, Input, OnInit } from '@angular/core';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html',
  styleUrls: ['./parent.component.css']
})
export class ParentComponent implements OnInit {
  isChild = true;
  name ="";
  constructor() { 
    console.log("Parent Constructor Called");
  }

  ngOnInit(): void {
    console.log("Parent ngOnInit called");
  }
  toggleChild(){
    this.isChild=!this.isChild;
  }
  
}
```
parent.component.html:
```html
<p><b>Parent works!</b></p>
<button (click)="toggleChild();">Child Component</button>
<input  type = "text" [(ngModel)] ='name' >
<app-child *ngIf="isChild" [name] = 'name'></app-child>
```

HTML page:

![ngOnChanges](/modules_new/resources/ngOnChangesChild.PNG)

HTML page after entering data into the text box(data-bound input change):

![ngOnChangesDataBoundInput](/modules_new/resources/ngOnChangesData.PNG)

- The `ngOnChanges` uses an object called SimpleChanges, using which the previous and current values can be obtained.
- SimpleChanges object is added to console.log.

child.component.ts

```ts
import { Component, OnDestroy, OnInit, OnChanges, SimpleChanges, Input } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit ,OnDestroy, OnChanges{

  @Input()
  name ='';

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
  }
  ngOnChanges(changes: SimpleChanges): void {
      console.log(changes)
      console.log("Child ngOnChanges called")
  }
  ngOnDestroy(): void {
      console.log("Child Component is Destroyed")
  }
  

}
```

HTML page:

![Simple Changes](/modules_new/resources/SimpleChanges.PNG)

4. `ngDoCheck()`: 
   
- Invoked when the change detector of a given component is invoked.
- Called immediately after `ngOnChanges()` on every change detection run and immediately after `noOnInit` after the first run.

- `ngDoCheck()` is implemented in child and parent component. A console.log statement is added.

child.component.ts

```ts
import { Component, OnDestroy, OnInit, OnChanges, SimpleChanges, Input, DoCheck } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit ,OnDestroy, OnChanges, DoCheck{

  @Input()
  name ='';

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
  }
  ngOnChanges(changes: SimpleChanges): void {
      console.log(changes)
      console.log("Child ngOnChanges called")
  }
  ngOnDestroy(): void {
      console.log("Child Component is Destroyed")
  }
  ngDoCheck(): void {
      console.log("Child ngDoCheck called")
  }
  

}
```

parent.component.ts

```ts
import { Component, DoCheck, Input, OnInit } from '@angular/core';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html',
  styleUrls: ['./parent.component.css']
})
export class ParentComponent implements OnInit, DoCheck {
  isChild = true;
  name ="";
  constructor() { 
    console.log("Parent Constructor Called");
  }

  ngOnInit(): void {
    console.log("Parent ngOnInit called");
  }
  toggleChild(){
    this.isChild=!this.isChild;
  }
  ngDoCheck(): void {
    console.log("Parent ngDoCheck called")
}
  
}
```

HTML image:

![ngDoCheck](/modules_new/resources/ngDoCheck.PNG)

HTML page after change:

![ngDoCheck after change](/modules_new/resources/ngDoCheckChanges.PNG)


5. `ngAfterContentInit()`: called only once after the first doCheck.

-  Content projection is done from parent component to child component.
-  Content in `<h3>` is projected to child component using <ng-content> in child component html.
- A template reference variable component is added in the parent component and access suing @ContentChild  in child component.
  
child.component.ts:

```ts
import { Component, OnDestroy, OnInit, OnChanges, SimpleChanges, Input, DoCheck, AfterContentInit, ContentChild } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit ,OnDestroy, OnChanges, DoCheck, AfterContentInit{

  @Input()
  name ='';
  @ContentChild('content') content:any; 

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
    console.log("Child ngOnInit "+ this.content)
  }
  ngOnChanges(changes: SimpleChanges): void {
      console.log(changes)
      console.log("Child ngOnChanges called")
      console.log("Child ngOnInit "+ this.content)
  }
  ngOnDestroy(): void {
      console.log("Child Component is Destroyed")
  }
  ngDoCheck(): void {
      console.log("Child ngDoCheck called")
      console.log("Child DoCheck "+ this.content)
  }
  ngAfterContentInit(): void {
      console.log("child  after content init")
      console.log("Child AfterContentInit "+ this.content)
  }
  

}
```

child.component.html:

```html
<p><b>Child works!</b></p>
<p>{{name}}</p>
<ng-content></ng-content>
```

parent.component.ts:

```ts
import { Component, DoCheck, Input, OnInit } from '@angular/core';

@Component({
  selector: 'app-parent',
  templateUrl: './parent.component.html',
  styleUrls: ['./parent.component.css']
})
export class ParentComponent implements OnInit, DoCheck {
  isChild = true;
  name ="";
  constructor() { 
    console.log("Parent Constructor Called");
  }

  ngOnInit(): void {
    console.log("Parent ngOnInit called");
  }
  toggleChild(){
    this.isChild=!this.isChild;
  }
  ngDoCheck(): void {
    console.log("Parent ngDoCheck called")
}
  

}
```

parent.component.html:

```html
<p><b>Parent works!</b></p>
<button (click)="toggleChild();">Child Component</button>
<input  type = "text" [(ngModel)] ='name' >
<app-child *ngIf="isChild" [name] = 'name'>
<h3 #content>Content Projection</h3>
</app-child>
```

HTML Page:

![ngAfterContentInit](/modules_new/resources/AfterContentInit.PNG)

- The `ngAfterContentInit()` is called after `ngDoCheck()` and the template referenceobject is not avilable till `ngAfterContentInit()` is invoked.

6. The `ngAfterContentChecked()`: called after `ngAfterContentInit()` and after every subsequent `ngDoCheck()`.

- The `ngAfterContentChecked()` is implemented in child component and a console.log statemnt is added.

child.component.ts:
```ts
import { Component, OnDestroy, OnInit, OnChanges, SimpleChanges, Input, DoCheck, AfterContentInit, ContentChild,AfterContentChecked } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit ,OnDestroy, OnChanges, DoCheck, AfterContentInit, AfterContentChecked{

  @Input()
  name ='';
  @ContentChild('content') content:any; 

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
    console.log("Child ngOnInit "+ this.content)
  }
  ngOnChanges(changes: SimpleChanges): void {
      console.log(changes)
      console.log("Child ngOnChanges called")
      console.log("Child ngOnChanges "+ this.content)
  }
  ngOnDestroy(): void {
      console.log("Child Component is Destroyed")
  }
  ngDoCheck(): void {
      console.log("Child ngDoCheck called")
      console.log("Child DoCheck "+ this.content)
  }
  ngAfterContentInit(): void {
      console.log("child  after content init")
      console.log("Child AfterContentInit "+ this.content)
  }
  ngAfterContentChecked(): void {
      console.log("child  after content checked")
  }
  
}
```

HTML page:

![ngAfterContentChecked](/modules_new/resources/AfterContentChecked.PNG)

7. `ngAfterViewInit()`: called once after `ngAfterContentChecked()`.

8. `ngAfterViewChecked()`: called after `ngAfterViewInit()` and every subsequent `ngAfterContentChecked()`.

- The `ngAfterViewInit()` and the `ngAfterContentChecked()` are implemented and console.log statements are added.

child.component.ts:

```ts
import { Component, OnDestroy, OnInit, OnChanges, SimpleChanges, Input, DoCheck, AfterContentInit, ContentChild,AfterContentChecked, AfterViewChecked, AfterViewInit } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit ,OnDestroy, OnChanges, DoCheck, AfterContentInit, AfterContentChecked, AfterViewInit, AfterViewChecked{

  @Input()
  name ='';
  @ContentChild('content') content:any; 

  constructor() {
    console.log("Child Constructor Called");
   }

  ngOnInit(): void {
    console.log("Child ngOnInit called");
    console.log("Child ngOnInit "+ this.content)
  }
  ngOnChanges(changes: SimpleChanges): void {
      console.log(changes)
      console.log("Child ngOnChanges called")
      console.log("Child ngOnChanges "+ this.content)
  }
  ngOnDestroy(): void {
      console.log("Child Component is Destroyed")
  }
  ngDoCheck(): void {
      console.log("Child ngDoCheck called")
      console.log("Child DoCheck "+ this.content)
  }
  ngAfterContentInit(): void {
      console.log("child  after content init")
      console.log("Child AfterContentInit "+ this.content)
  }
  ngAfterContentChecked(): void {
      console.log("child  after content checked")
  }
  ngAfterViewInit(): void {
    console.log("child  AfterViewInit")  
  }
  ngAfterViewChecked(): void {
    console.log("child  AfterViewChecked")  
  }

}
```

HTML page:
![ngAfterView](/modules_new/resources/ngAfterView.PNG)
















</details>
<details><summary>Summary</summary> 

# Summary

Angular Lifecycle hooks describe the life cycle of a Component.

- Component lifecycle starts with `constructor()` followed by eight lifecycle hooks.

1. **`ngOnChanges`**: When an input/output binding value changes.
2. **`ngOnInit`**: After the first `ngOnChanges`.
3. **`ngDoCheck`**: Developer's custom change detection.
4. **`ngAfterContentInit`**: After component content initialized.
5. **`ngAfterContentChecked`**: After every check of component content.
6. **`ngAfterViewInit`**: After a component's views are initialized.
7. **`ngAfterViewChecked`**: After every check of a component's views.
8. **`ngOnDestroy`**: Just before the component/directive is destroyed.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
