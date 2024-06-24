# Implementation


- A method display text that gives an alert message when the string is empty is created in a service named display.

- The service is injected into the app component.

to create service the following command is written:

```properties
ng generate service display
```

display.service.ts

```ts
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class DisplayService {


  constructor() { }
  displayText(text:string):void{
    if(text===""){
      alert("please enter the text!");
    }

  }
}

```

app.component.ts

```ts
import { Component,  OnInit } from '@angular/core';
import { DiaplayService } from './diaplay.service';


@Component({
  selector: 'app-root',
  templateUrl:'./app.component.html',
  styleUrls: ['./app.component.css'],
  providers: [DisplayService],
})
export class AppComponent  {
  title = "Sample";
  value ="";

  constructor(private display:DisplayService){}

  onClick():void{
    this.display.displayText(this.value);
  }
  
}

```

app.component.html

```html
<input type="text" [ngModel] = "value" placeholder="enter text">
<button (click)="onClick();">Submit</button>
```

HTML page:

![Dependency Injection](/modules_new/resources/DependencyInjection.png)