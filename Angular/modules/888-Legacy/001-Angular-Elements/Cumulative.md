# Cumulative for the  Angular Elements
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Angular Elements.
</details>
<details><summary>Description</summary>

# Description

### Angular Elements

Angular elements are used to package Angular components as custom elements, a web standard for defining new HTML elements.

- A registry is maintained by the browser to keep track of all the custom elements.
- The registry is mapped to a JavaScript class which controls the behaviour and output of the element.
- Angular elements are part of the `@angular/elements` package.
- `createCustomElement()` function is used to create a custom element.

### Advantages of using Angular Elements.

1. Code Reusability: Angular components can be used in other frameworks and libraries, such as React and Vue etc.
2. Using Angular on Serve Side: Angular which is a front-end framework can be added to the project's backend.
3. Publish parts of the Application: Angular elements can be used to develop and publish parts of an application independently.
</details>
<details><summary>Real World Application</summary>

# Real World Application

Real World applications of Angular elements :

1. Put an Angular component inside other JavaScript Libraries/Frameworks like React and Vue.
2. Passing data from Vue and react into the Angular Component.
3. Use the Angular 14 component in an AngularJS app.
</details>
<details><summary>Implementation</summary> 

# Implementation

Create a new component named universe.

```properties
ng generate component universe
```

universe.component.html:

```html
<p>Universe is Infinite</p>
```

Installing  web components for browser Compatability:

```properties
npm install @webcomponents/custom-elements --save
```

Importing modules in polyphiss.ts

```ts
import '@webcomponents/custom-elements/src/native-shim'
import '@webcomponents/custom-elements/custom-elements.min'  
```

**Converting component to the custom element:**

1. Importing `Injector` from `@angular/core`
2. Importing `createCustomElement` from `@angular/elements`.
3. Adding UniverseComponent to entryComponets in NgModule.
4. Adding Injector to the contractor.
5. Implementing `ngDoBootStrap()`
6. Passing UniverseComponent to `createCustomElement()` method.
7.  This method serves as a bridge to convert angular components to custom elements and deal with native DOM API.
8.  Registering it by using `customElemnts.define()`.


app.module.ts
```ts
import { NgModule, Injector } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import {createCustomElement} from '@angular/elements';
import { AppComponent } from './app.component';
import { UniverseComponent } from './universe/universe.component';


@NgModule({
  declarations: [
    AppComponent,
    UniverseComponent,
  ],
  imports: [
    BrowserModule,
    FormsModule
  ],
  entryComponents:[UniverseComponent],
  providers: [],
  bootstrap: []
})
export class AppModule { 
  constructor(private injector: Injector) {}
  ngDoBootstrap(){
    const el = createCustomElement(UniverseComponent, {injector: this.injector});
    customElements.define('app-universe', el);
  }
}

```

9. Adding `<app-universe>` tag directly in index.html.

```html
<app-universe></app-universe>
```

HTML page:

![Angular Element](/modules_new/resources/AngularElements.png)






</details>
<details><summary>Summary</summary> 

# Summary

- Angular elements are used to convert Angular components into custom elements.
- `createCustomElement()` method of `@angular/elements` package is used to convert an Angular compoennt to custom element.
- Custom elements in Angular can be used in Angular JS, Vue and React.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
