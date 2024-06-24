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


