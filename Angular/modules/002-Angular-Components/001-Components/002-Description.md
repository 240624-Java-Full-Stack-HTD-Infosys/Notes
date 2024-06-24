# Description

## Component 
Components are building blocks of Angular applications.

A component consists of:
1. An HTML template.
2. A TypeScript class that defines the behaviour of the component.
3. Optional CSS Styles applied to the template


### Advantages of Angular Components
- Using Angular Components a Single Page Application can be created.
- Angular components are independent. So, if an error occurs with one component, the functionality of the other component might not be affected.
- Angular components support lazy loading (only components necessary at a particular time are loaded and the Application runs smoothly).
- As Angular Components are independent, it is easy to maintain the code.

**Component Decerator**
- `@Component`, is the component decorator which marks the class as an Angular component and provides metadata about how the component works during the runtime.
- Every Angular Project has a default component called, app.component.

* **app.component.css** -  holds all the CSS styles 
* **app.component.html**  -  this template contains typical HTML elements and alters the HTML based on our app's logic and DOM manipulations. 
* **app.component.ts** -  contains typescript code to control the component behaviour.

Let's have a look at the app.component.ts file under the app folder and understand the code behind the root component of the application.

```typescript
import { Component } from '@angular/core';

 @Component ({
 selector: 'app-root',
 templateUrl: './app.component.html' ,
 styleUrls: ['./app.component.css']
 })
 export class AppComponent {
 title = 'my first app';
 } 
```
In this file, we export the *AppComponent* class, and we decorate it with the `@Component` decorator, imported from the `@angular/core` package, which takes a few metadata, such as:

-  **selector:** A CSS selector that tells Angular to create and insert an instance of this component wherever it finds the corresponding tag in template HTML. For example, if an app's HTML contains <app-root></app-root>, then Angular inserts an instance of the AppComponent view between those tags.

- **templateUrl:** The module-relative address of this component's HTML template. Alternatively, you can provide the HTML template inline, as the value of the **template** property. 

-  **styleUrls:** This is an array of relative paths to where the component can find the styles used to style the HTML view. Alternatively, you can provide the CSS Style inline, as the value of the **styles** property.


- A component must belong to the `Ng Module`, for it to be available for another component.

### How to create a component in Angular?

Run the `ng generate component <component_name>` or `ng g c <component-name>` command in the terminal to create a component.

