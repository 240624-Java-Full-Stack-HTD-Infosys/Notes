# Cumulative for the  Directives and Components
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Directives.
</details>
<details><summary>Description</summary>

# Description

### Directives

 A Directive is a custom HTML element or attribute used to power up and extend our HTML 

- Directives fall into one of three categories
    - Component Directive: established in the selector attribute of the @Component decorator 
    - Structural Directive: changes the structure or layout of a view by manipulating, adding, or removing elements and their children 
        - `*ngIf`: takes a boolean expression and makes an entire chunk of the DOM appear or disappear (exposed in BrowserModule)
        - `*ngFor`: used to create for loops, at minimum needs a looping variable and a list (exposed in BrowserModule)
        - `ngSwitch` : (actually a set of directives and ngSwitch is an attribute directive since it controls the behaviour of *ngSwitchCase and *ngSwitchDefault)
            - ngSwitch
            - *ngSwitchCase
            - *ngSwitchDefault
    - Attribute Directive: listens to and modifies the behaviour of other elements, attributes, properties, and components. However, usually applied to attributes 
        - NgClass : adds and removes a set of CSS classes 
        - NgStyle : adds and removes a set of HTML styles
        - NgModel : allows for two-way data binding to an HTML form element (exposed in FormsModule)

### Differences between Directives and Components

In a short note, A component(@component) is a directive-with-a-template.

- Some of the major differences are mentioned in a tabular form

    | Component | Directive |
    |---- | ---------
    | To register a component we use @Component meta-data annotation  | To register directives we use @Directive meta-data annotation |
    | Components are typically used to create UI widgets| Directive is used to add behaviour to an existing DOM element |
    | Component is used to break up the application into smaller components| Directive is used to design re-usable components|
    | Only one component can be present per DOM element | Many directives can be used per DOM element |
    | @View decorator or templateurl/template are mandatory | Directive doesn't use View|



<br>
<i> <b>Note</b>: detailed explanation about attribute directives and structural directives will be given in the upcoming modules.</i> 
</details>
<details><summary>Real World Application</summary>

# Real World Application

Any common functionality can be declared in a directive and implemented anywhere in the Angular application.

The following are a few real-time examples of Angular directives.

- Autofocus on input fields
- Async email/username validators
- Autosize for textareas
- Debounce directive for input fields
- Infinite scroll
- Sticky directive (makes an element fixed position when it reaches a certain scrolling distance)


</details>
<details><summary>Implementation</summary> 

# Implementation


## User-Defined Directive

Consider my highlight directive which highlights the text on the HTML page, when the user hovers the mouse on the text.

A directive named Highlight is created by running the below line in the terminal.

```properties
ng generate directive highlight
```

highlight.directive.ts

```ts
import { Directive, HostListener, ElementRef } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {

  constructor(private e: ElementRef) {  
  }  

  @HostListener('mouseover') onMouseOver() {  
    this.changeBackgroundColor('blue');  
  }

  @HostListener('mouseleave') onMouseLeave() {  
    this.changeBackgroundColor('white');  
  }  

  private changeBackgroundColor(color: string) {  
    this.e.nativeElement.style.backgroundColor = color;  

  }    

}
```

app.component.html:

```html
<p appHighlight>Highlight me!</p>
```

HTML page:

![Highlight Directive](/modules_new/resources/highlight1.png)

The HTML page on mouse hover:

![Highlight Directive on mouse hover](/modules_new/resources/highlight2.png)


# Built-in Directive

Angular has many built-in directives. Unlike the user define directives the implementation for the built-in directives is predefined in Angular.

Consider two `div` tags with a built-in structural directive `*ngIf`.

app.component.html:

```html
<div *ngIf= "true" >  
    Condition is true!
    </div>  
<div *ngIf="false">
    Condition is False!
</div>
```

The statement in `div` block with the condition true will be in DOM. 

HTML page:

![Built-in Directive](/modules_new/resources/Built-in_Directive.png)


<i> <b>Note</b>: Explanation and implementation for attribute directives and structural directives will be given in the upcoming modules.</i> 
</details>
<details><summary>Summary</summary> 

# Summary

- Directives are classes that add additional behaviour to the elemnts in Angular applications.
- Directives can be created by running `ng new directive <directive-name> ` using Angular CLI.
- A directive class is annotated with `@Directive`.
- Component Directives, Attribute Directives and Structural directives are the different types of directives used in Angular.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
