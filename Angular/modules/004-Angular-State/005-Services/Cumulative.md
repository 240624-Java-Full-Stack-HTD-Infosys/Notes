# Cumulative for the  Services
<details><summary>Description</summary>

# Description

**Service** : A TypeScript class to share data or functionality throughout the application.

Uses of service:

- Code reuse
- Cross-component communication

**Dependency injection**: A coding pattern in which a class receives the instances of the objects it needs (called dependencies) from an external source rather than creating them itself.

A service can be created and injected in the following steps:

1. Create a class and decorate it with the @Injectable decorator and export it.

1. Register the provider => a provider is a code that can create or return a service 
    - We can add the service to the provider's property in either:
      - @Component => Injectable to component and its children. 
      - @NgModule => Injectable everywhere in an application .
2. Inject the Service
    - We achieve dependency injection in the constructor of the class in which we wish to use the service. 
    - Similar to Java, every class has an implicit no-arg constructor if no other constructor is defined.
    - To inject dependencies, we need an explicit constructor passing in the service to be injected. 

 ```ts
    export class MyComponent {
                constructor(private myService: MyService) {}
            }
```

        
            




</details>
<details><summary>Real World Application</summary>

# Real World Application

- Encapsulating common functions and values in a service and injecting them as dependencies in different components achieves loose coupling in Angular. This approach promotes maintainability and reduces the risk of errors. An example of this is using a service to display an alert message when an input field is left empty.
</details>
<details><summary>Implementation</summary> 

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
</details>
<details><summary>Summary</summary> 

# Summary

- Dependency injection is a programming technique where a class receives the necessary objects or dependencies from an external source instead of creating them itself. This allows for more flexible and decoupled code, as the class is not tightly coupled to specific implementations of its dependencies. Instead, dependencies can be swapped out or replaced without requiring changes to the class that uses them.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
