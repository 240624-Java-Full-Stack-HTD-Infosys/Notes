# Description
Angular modules is a system to organize code based on application domain, workflow, or related capabilities. That is, a way to group closely related code. The Angular Modules system, often simply refered to as "ngModules" shouldn't be confused with the JavaScript concept of modules. Unless otherwise indicated, the word "module" in these notes refers to ngModules.

## ngModules and Standalone Components
In older versions of Angular every SPA had at least one ngModule, the root module located in the file `app.module.ts`. As of version 17 new Angular projects do not require a root module, and by default will not include one. You will see many examples which predate this change where all components exist within an ngModule. Now, components can exist outside ngModules. These are called "Standalone Components" and are the default way of organizing components going forward.

This change was due to the bloated size of Angular apps. It was decided to streamline dependency bloat by reducing the reliance on the ngModules system for dependency management. Instead of supplying all dependencies to all components in a module, dependencies are injected only into the components where needed.

Angular modules can still be used in version 17, but they are no longer the preferred approach.

## ngModules
NgModules are TypeScript classes decorated with the [@NgModule](https://angular.io/api/forms/NgModel) decorator imported from the `@angular/core` package.

NgModule takes metadata and describes how to compile a component's template and how to create an injector at runtime. It identifies the module's components, directives, and pipes and makes them public through the export property which can be used by external components.

Prior to version 17, the Angular CLI generates the basic *AppModule* (src/app/app.module.ts file) when creating a new application. From 17 onward in order to create a project with a root module, use the flag `--no-standalone`.

`@NgModule` takes the below metadata to launch the application:

- **declarations** —  contains a list of components, directives, and pipes, which belong to this module. 

- **imports** —  contains a list of modules, which are used by the component templates in this module reference.  For example, we import *BrowserModule* to have browser-specific services such as DOM rendering, sanitization, and location. 

- **providers** — the list of service providers that the application needs.

- **bootstrap** — contains the root component of the application.
