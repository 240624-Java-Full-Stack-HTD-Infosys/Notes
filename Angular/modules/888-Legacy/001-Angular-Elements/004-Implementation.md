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






