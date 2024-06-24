# Cumulative for the  Directives
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Angular Structural directives.


</details>
<details><summary>Description</summary>

# Description

## Structural directives

Structural directives are used for adding, removing, or manipulating DOM elements. Structural directives start with an asterisk (*) followed by a directive name.  There are three built-in structural directives - `ngIf`, `ngFor` and `ngSwitch`.

### ngIf Directive

The `*ngIf` directive allows us to add or remove DOM Elements based upon the Boolean expression. It doesn't hide the elements, but generally adds or removes them physically from the DOM.

### ngFor Directive

 The `*ngFor` directive is used to repeat a part of the HTML template once per each item from an iterable list.

### ngSwitch Directive

The Angular *NgSwitch* has a set of cooperating directives: `NgSwitch`, `NgSwitchCase`, and `NgSwitchDefault`.

The syntax for `ngSwitch` Directive:

```html
<container_element [ngSwitch]="switch_expression">  
    <inner_element *ngSwitchCase="match-1">...</inner_element>  
    <inner_element *ngSwitchCase="match-2">...</inner_element>  
    <inner_element *ngSwitchCase="match-3">...</inner_element>  
    <inner_element *ngSwitchDefault>...</inner_element>  
</container_element>
``` 
NgSwitch* is an attribute directive that controls the behaviour of the other two switch structural directives - *NgSwitchCase* and *NgSwitchDefault*. That's why we write *NgSwitch* as `[ngSwitch]`, *NgSwitchCase* as `*ngSwitchCase`, and *NgSwitchDefault* as `*ngSwitchDefault`.

*NgSwitchCase* displays its element when its value matches the switch value. *NgSwitchDefault* displays its element when no sibling *NgSwitchCase* matches the switch value.

### `<ng-template>`  

Structural directives can work with the HTML5 `<ng-template>` element, which is designed to hold template code. 




</details>
<details><summary>Real World Application</summary>

# Real World Applications

- Consider that you need to show or hide content based on the user role. it can be done using the `*ngIf` structural directive.
- The `*range` directive can be used to take input in specific ages, like users with ages above 18 are allowed to use the page etc.
- The `ngSwitch` can be used in filter options. It can be used to display only specific options as per the choice of the user.
- After filtering the options using `*ngSwitch` the unordered list of the category can be displayed using `*ngFor`.
</details>
<details><summary>Implementation</summary> 

# Implementation

### 1. ngIf:

The paragraph with `*ngIf` condition true is displayed.

```html
<p *ngIf="true">
  The expression is true, this paragraph is in DOM.
</p>
<p *ngIf="false">
  Expression is false, this paragraph is not in DOM.
</p>
```

HTML page:

![ngIf](/modules_new/resources/ngIf-1.png)


We can also have an else block associated with a *ngIf directive.

If the `*ngIf` condition is false the elseBlock is implmented.

```html
<div *ngIf="5>10 else elseBlock">  
5 is greater than 10...
</div>  
<ng-template #elseBlock>  
10 is greater than 5... 
</ng-template> 
```

HTML page:

![ngIf](/modules_new/resources/ngIf-2.png)

### 2. ngFor:

The `*ngFor` is used to iterate through the customer object instances.

app.component.ts

```ts
import { Component } from '@angular/core';

@Component({
 selector: 'app-root',
 templateUrl: './app.component.html',
 styleUrls: ['./app.component.css']
})
export class AppComponent {
 customers : Customer[] = [
   {id : 234 , name: 'John'},
   {id : 235 , name: 'Adam'},
   {id : 236 , name: 'Nick'}
 ];
}
class Customer { 
 id:number;
 name: string;
} 
```

app.component.html
```html
<table>
<tr *ngFor="let customer of customers;">
    <td>{{customer.id}}</td>
    <td>{{customer.name}}</td>   
</tr>
</table>
```

HTML page:

![ngFor](/modules_new/resources/ngForExample.png)


### 3. switch:

The `*ngSwitch` has different cases. If any case is satisfied, the statement in `div` tag associated with that case is displayed.

app.component.html

```html
<div class = 'input-num'>
Enter the number<input type='text' [(ngModel)]="num" />
</div>
<div [ngSwitch]="num">
  <div *ngSwitchCase="'1'">You entered - One</div>
  <div *ngSwitchCase="'2'">You entered - Two</div>
  <div *ngSwitchCase="'3'">You entered - Three</div>
  <div *ngSwitchCase="'4'">You entered - Four</div>
  <div *ngSwitchCase="'5'">You entered - Five</div>
  <div *ngSwitchDefault> ...default </div>
</div>
```

- Declare num in app.component.ts.

```ts
import { Component } from '@angular/core';

@Component({
 selector: 'app-root',
 templateUrl: './app.component.html',
 styleUrls: ['./app.component.css']
})
export class AppComponent {
num =0;
}
```

HTML page:

![ngSwitch](/modules_new/resources/ngSwitch-1.png)

![ngSwitch](/modules_new/resources/ngSwitch-2.png)





</details>
<details><summary>Summary</summary> 

# Summary

- Structural directives are used to add, delete and modify the DOM elements.
- Every structural directive starts with an "*".
- Few commonly used structural directives are:
    - `ngIf`
    - `ngFor`
    - `range` 
    - `ngSwitch`
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
