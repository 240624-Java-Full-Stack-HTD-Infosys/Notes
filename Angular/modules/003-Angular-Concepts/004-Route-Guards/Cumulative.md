# Cumulative for the  Route Guards
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The Basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Route guards.


</details>
<details><summary>Description</summary>

# Description

Angular Route guards can be used to control weather the user can navigate to or away from the giver route based on some condition. In simpler terms an Angular Route guard is used to secure a route.

### Uses of Route guard:


- To confirm the navigation operation
- Asking weather to save data before moving away from the view.
- Allow access to certain parts of the application to specific users.
- Validating the route parameters before navigating to the route.
- Fetching some data before you display the component view.

### Types of Route guards in Angular

1. `CanActivate`: Decides if a route can be activated or not based on a given condition. 
2. `CanDeactivate`: Checks criteria before leaving a route
3. `Reslove`: Used to prefetch data before we navigate to a route
4. `CanLoad`: Decides if children can be loaded or not
5. `CanActivateChild`: Similar to the `canActivate` guard except that it is called when activating a route child and not the route itself.



</details>
<details><summary>Real World Application</summary>

# Real World Application

- Simple scenario where a route gaurd is a used is not allowed to navigate all parts of the application if user is not logged in.
- Autentication is also an important application. Consider udemy or amazon or uber, a user is not allowed to but a course/ buy a product/ book a ride unless the user is logged in.
- If the user is not logged in they are redirected to login/signup page.
</details>
<details><summary>Implementation</summary> 

# Implementation

**Step 1:**
- Creating a guard service.

**Step 2:**
- This class should implement any route guard interface.

```ts
import { CanActivate } from "@angular/router";

export class RouteGuardService implements CanActivate{
    

}
```

**Step 3:**
- The service class should implement the method of the route guard interface.
- The route guard method returns a boolean value.
- If it returns true the navigation is allowed else the navigation process is stopped.

```ts
import { ActivatedRouteSnapshot, CanActivate, RouterStateSnapshot, UrlTree } from "@angular/router";
import { Observable } from "rxjs";

export class RouteGuardService implements CanActivate{
    canActivate(route:ActivatedRouteSnapshot, state:RouterStateSnapshot): boolean{
        return true;
    }
}
```

**Step 4:**
- The service created should be provided using the providers array in app module.

app.module.ts

```ts
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppComponent } from './app.component';
import { RouteGuardService } from './routegaurd.service';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [RouteGuardService],
  bootstrap: [AppComponent]
})
export class AppModule { }
```


**Step 5:**

- The created route guard service is used in any route in the application.

app.routing.module.ts



```ts
{path: 'pathName', component: componentName, canActivate: [RouteGuardService] },
```



</details>
<details><summary>Summary</summary> 

# Summary

- Route guards are used to secure a route based on some condition.

Types of Route guards in Angular:

1. `CanActivate`
2. `CanDeactivate`
3. `Reslove`
4. `CanLoad`
5. `CanActivateChild`
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
