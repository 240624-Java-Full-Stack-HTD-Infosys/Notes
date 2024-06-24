# Cumulative for the  Dependency Injection
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Dependency Injection.


</details>
<details><summary>Description</summary>

# Description
Dependency Injection is a programming pattern where dependencies are created outside of the object which needs them, and then provided by passing the dependency into a setter or constructor. There are a few DI systems in Angular, and several ways to get dependencies injected. 

## Providers and Consumers
There are two main roles when we look at DI in Angular, providers and consumers. Consumers are those things which require a dependency to work, generally the consumers are components. Providers make dependencies available for consumers. In order to get a dependency into where it is needed we will need to both provide it and inject it.

### A note about imports:
We aren't considering the `import` and `export` keywords here. You must always use `export` and `import` to make javascript or typescript code available in a different file. `import` statements won't be included in the code examples shown.

## Providing Dependencies
There are several ways to provide dependencies, and there are some unique behaviors depending on which method we choose.

### via @Component decorator
We can provide a dependency directly to a component, making it available for that component. **Note: Using this method will result in a new instance of the dependency every time it is injected. Be careful not to use this method to provide shared resources or singletons, they won't work as intended!**
Add dependency into optional providers array of component decorator. This will provide multiple instances of that dependency, not singleton!

Include the dependency in the optional `providers` array of the `@Component` decorator.

```typescript
@Component({
  selector: 'app-child',
  standalone: true,
  imports: [],
  templateUrl: './child.component.html',
  styleUrl: './child.component.css',
  providers: [GlobalStateService]
})
export class ChildComponent {
    //...
}
```
In the above example we have provided the `GlobalStateService` class to the `ChildComponent` class. We have only made it available to this class, we have not yet injected it.



### via @NgModule decorator
If using NgModules we can provide dependencies in a similar manner to the @Component decorator, using the `@NgModule` decorator. Unlike above, there is no need to worry about this method creating multiple instances of a dependency. This method is compatible with singletons and shared services. To provide a dependency this way use the `providers` array of the `@NgModule` decorator:

```typescript
@NgModule({
  declarations: [
    AppComponent,
    ChildComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [GlobalStateService],
  bootstrap: [AppComponent]
})
export class AppModule { 
    //...
}
```
The GlobalStateService dependency is provided to all components which are part of the `AppModule`. In this example the dependency is effectively global, as `AppModule` is the root module of a non-standalone project. As of version 17 of Angular there is no longer a root module by default.

### via boostrapping
From Angular 17 onward NgModules are becomming obsolete, and new projects will not have a root module by default. Instead of bootstrapping the root module, we bootstrap the application and provide an `ApplicationConfig` object. This config object (located in `app.config.ts` by default) contains a `providers` array similar to those above.

Config object located in `app.config.ts`:
```typescript
export const appConfig: ApplicationConfig = {
  providers: [GlobalStateService]
};
```

This is used in `main.ts`:
```typescript
bootstrapApplication(AppComponent, appConfig)
  .catch((err) => console.error(err));
```

According to the Angular docs, the next method is preferred to this one due to an optimization technique called "tree-shaking". Whenever you can, you should use `@Injectable` instead. See below.

### via @Injectable decorator
In the previous examples we have been providing the `GlobalStateService` via different methods. By default, services are generated with the `@Injectable` decorator, making them injectable. `@Injectable` can actually provide the dependency directly. By default you don't actually need to provide a service, as it is already provided everywhere using the `providedIn` property.

```typescript
@Injectable({
  providedIn: 'root'
})
export class GlobalStateService {
    //...
}
```
This provides our service at the application level thanks to the alias 'root', which is the default `EnvironmentInjector`. For more information, see the Angular docs.

## Injecting Dependencies
Providing the dependencies is just the first step. Thankfully, injecting dependencies is easier. The most commonly used method is to include your dependency in the constructor of dependent class. Angular will then inject the dependency based on the listed type.

```typescript
@Component({
  selector: 'app-child',
  standalone: true,
  imports: [],
  templateUrl: './child.component.html',
  styleUrl: './child.component.css',
  providers: [GlobalStateService]
})
export class ChildComponent {
    globalStateService: GlobalStateService;

    constructor(globalStateService: GlobalStateService) {
        this.globalStateService = globalStateService;
    }
}
```
Here Angular will identify the necessary dependency by it's type, `GlobalStateService`, and inject it when the constructor is invoked. Then, in the constructor, we assign that dependency to the local `globalStateService` variable.

Less popular would be the `inject()` method:
```typescript
@Component({
  selector: 'app-child',
  standalone: true,
  imports: [],
  templateUrl: './child.component.html',
  styleUrl: './child.component.css',
  providers: [GlobalStateService]
})
export class ChildComponent {
    globalStateService: GlobalStateService = inject(GlobalStateService);
}
```
</details>
<details><summary>Summary</summary> 

# Summary

- Dependency injection is a programming pattern where a class receives the necessary objects or dependencies from an external source instead of creating them itself
- There are several ways to provide and inject dependencies in Angular
   - `providers` array at the component, module, or application level
   - `providedIn` property of `@Injectable`
   - `providers` array in the `ApplicationConfig` object passed to `bootstrapApplication()`
</details>
