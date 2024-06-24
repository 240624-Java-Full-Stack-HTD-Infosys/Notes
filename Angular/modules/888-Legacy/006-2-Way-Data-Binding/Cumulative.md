# Cumulative for the  2 Way Data Binding
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define two way binding.
</details>
<details><summary>Description</summary>

# Description

## 2-way binding
Conventionally two-way binding is achieved by combining property binding/text interpolation and event binding, but in Angular, this is achieved by "[()]". Two-way binding is used to listen for events and update values.

![Two Way Binding](/modules_new/resources/TwoWayBinding.PNG)
</details>
<details><summary>Real World Application</summary>

# Real World Applications

- while setting a new password, based on the password rules, dynamically the data is transferred to the model and checked if all the conditions are satisfied, and the data is transfered from model to view, to inform the user.
</details>
<details><summary>Implementation</summary> 

# Implementation


**Two-Way Binding**

- A code to display the text entered by the user and a clear button to clear the text.

app.component.html:

```html
<label>Enter Text:</label><br>
<input type="text" name="value" [(ngModel)]="value">
<p>{{value}}</p>
<button (click)="clearValue()">Clear</button>
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
  
  title = "Template literal works!";
  onSave():void{
    alert("Information Saved!");
  }
  value="";
  clearValue() {
    this.value="";
  }
  
}

```

app.module.ts

```ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';
import { ParentComponent } from './parent/parent.component';
import { ChildComponent } from './child/child.component';
import { FormsModule } from '@angular/forms';

@NgModule({
  declarations: [
    AppComponent,
    ParentComponent,
    ChildComponent
  ],
  imports: [
    BrowserModule,
    FormsModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

<b>Note:</b><i> FormsModule should be imported in app.module.ts file and "FormsModule" should be added to imports of NgModule to use ngModel.</i>

HTML page while typing some text:

![2 way binding](/modules_new/resources/twowaybinding-1.png)

HTML page after clicking on clear button:

![2 way binding](/modules_new/resources/twowaybinding-2.png)


</details>
<details><summary>Summary</summary> 

# Summary

- In two way binding data is transferred from HTML (Template) to TypeScript (Model) and vice-versa.

</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
