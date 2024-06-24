# Cumulative for the  Attribute Directives
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Angular Attribute directives.


</details>
<details><summary>Description</summary>

# Description

**Attribute Directives**

Attribute Directives are used to modify the properties of DOM.

Examples of Attribute Directives:

1. `ngClass`
2. `ngStyle`
3. `ngModel`

A custom attribute directive can be created by creating a directive as below.

```properties
ng generate directive <directive name>
```

### ngClass Directive

The `[ngClass]` directive is used for adding or removing the CSS classes on an HTML element. It allows us to apply CSS classes dynamically based on expression evaluation. 

**Syntax:** `<some-element [ngClass]="value"> ....</some-element>`

The value can be:
-  **string** - the CSS classes declared as string. For example, `<some-element [ngClass]="'first second'">...</some-element>` where `first` and `second` are the two CSS Classes delimited by space. Both the `first` and `second` CSS styles will be applied to the element.

- **Array** - the CSS classes declared as Array elements. For example,`<some-element [ngClass]="['first', 'second']">...</some-element>` .

- **Object** - in which *keys* are CSS classes and *values* are expression that  evaluates true or false.  The CSS Class is applied to the element when the expression evaluates a truthy value, else they will be removed. For example,`<some-element [ngClass]="{'first': true, 'second': true, 'third': false}">...</some-element>`.

### ngStyle Directive

The `[ngStyle]` directive allows us to dynamically change the style of the HTML element based on the expression.

**Syntax:** `<some-element [ngStyle]="objExp">...</some-element>`

### Custom Directives

We can create our custom directives to use in the Angular component with the CLI command `ng generate directive <name of the directive>`.

**For example**, When we run this command `ng generate directive text` in a terminal, the CLI creates a *text.directive.ts* file and corresponding test file *text.directive.spec.ts* under *src/app* folder in our application. Also, CLI declares this directive class under *AppModule*.





</details>
<details><summary>Real World Application</summary>

# Real World Application

- Attribute directives are used anytime you want logic or events to change the appearance or behaviour of the view. 
- Dropdowns, accordions, and tabs are common use cases for custom attribute directives.
-  if there is a UI element that is common throughout your app, An attribute directive can be implemented to share it across components and modules to avoid repeating the code for the same functionality.
</details>
<details><summary>Implementation</summary> 

# Implementation

### 1. ngClass Directive:
The CSS classes in the app.component.css file:

```css
.red { 
    background-color: red;
}
.size20 {
    font-size: 20px; 
    font-style: italic;
}
```

Using the [ngClass] directive in the app.template.html file, to add or remove CSS Classes on the element.

```html
<h3 [ngClass]="'red'"> Need your attention</h3>
<div [ngClass]="['red','size20']"> Red Background, Text with Size 20px  </div>
<div [ngClass]="{'red':false,'size20':true}">Text with Size 20px</div>
```

HTML page:

![ngClass](/modules_new/resources/ngClass.png)

### 2. ngStyle Directive:

app.component.html

```html
Enter the username: <input type = 'text' [(ngModel)] = 'name'>
<div [ngStyle]="{'background-color':username === 'Admin' ? 'green' : 'red' }"></<div>
```

HTML page:
 
 ![ngStyle](/modules_new/resources/ngStyles1.png)

HTML page:
![ngStyle](/modules_new/resources/ngStyles2.png)

 ### 3. Custom Directives:

 When the command `ng generate directive text` is run in the terminal.

 text.directive.ts

 ```ts
 import { Directive} from '@angular/core';

@Directive({
  selector: '[appText]'
})
export class TextDirective {
    //You can add custom styling of DOM Elements here...
    constructor() {
    
    }
}

```




</details>
<details><summary>Summary</summary> 

# Summary

- Attribute directives are used to modify the DOM,
- `ngClass`, `ngStyle` and `ngModel` are built-in Angular attribute directives.
- Custom directives can be created in Angular CLI by running the command `ng generate directive text`.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
