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




