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



