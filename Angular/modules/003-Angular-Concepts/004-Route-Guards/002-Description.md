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



