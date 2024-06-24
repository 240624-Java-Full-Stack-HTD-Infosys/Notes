# Cumulative for the  Hello Angular
<details><summary>Description</summary>

# Angular - Angular Hello

## Contributors

Author: Jonathan De La Cruz
Reviewers:

## Prerequisites

- HTML/CSS/JS familiarity
- TypeScript familiarity
- NodeJS
- NPM package manager (Should be bundled with NodeJS, have associates verify their installations)
- VSCode
- Angular CLI

## How to Complete

### 1. Creating an Angular Project with the CLI

1. Open up a terminal or command prompt and navigate to the directory where you want to create your project.
2. Run the following command:

   ```console
   ng new my-angular-app
   ```

   This will create a new Angular project in a directory called "my-angular-app". Go ahead and add angular routing when prompted, and just select CSS for styling for now. For this coding activity, it won't matter. But in the future you can choose between different flavors of style languages to use.

3. Once the project is created, navigate into the directory by running:

   ```console
   cd my-angular-app
   ```

4. Run the following command to start the development server:

   ```console
   ng serve
   ```

5. Open your web browser and navigate to `http://localhost:4200/`. You should see the default Angular app homepage.

### 2. Statically Rendering a Component

1. In the `src/app` directory, create a new file called `hello-world.component.ts` and add the following code:

    ```typescript
      import { Component } from '@angular/core';

      @Component({
        selector: 'app-hello-world',
        template: '<h1>Hello, world!</h1>'
      })
      export class HelloWorldComponent {}
    ```

   This code defines a new Angular component that renders a simple "Hello, world!" message.

2. Next, open up `app.module.ts` in the `src/app` directory and add `HelloWorldComponent` to the `declarations` array:

    ```typescript
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';

    import { AppComponent } from './app.component';
    import { HelloWorldComponent } from './hello-world.component';

    @NgModule({
      declarations: [
        AppComponent,
        HelloWorldComponent
      ],
      imports: [
        BrowserModule
      ],
      providers: [],
      bootstrap: [AppComponent]
    })
    export class AppModule {}
    ```

   This code imports `HelloWorldComponent` and adds it to the `declarations` array so that it can be used in the app.

3. Finally, open up the `app.component.ts` file in the `src/app` directory and modify it to include the `HelloWorldComponent`. Replace the contents of the file with the following code:

    ```typescript
      import { Component } from '@angular/core';

      @Component({
        selector: 'app-root',
        template: `
          <h1>Welcome to my Angular app!</h1>
          <app-hello-world></app-hello-world>
        `
      })
      export class AppComponent {}
    ```

   This code defines the main app component that renders the "Welcome to my Angular app!" message and includes the `HelloWorldComponent`.

4. Save all of the files and refresh the page in your web browser. You should now see both the "Welcome to my Angular app!" message and the "Hello, world!" message.

### 3. Using Dynamic Component Rendering with Routes

1. In the `src/app` directory, create a new file called `about.component.ts` and add the following code:

    ```typescript
      import { Component } from '@angular/core';

      @Component({
        selector: 'app-about',
        template: '<h2>About page</h2>'
      })
      export class AboutComponent {}
    ```

   This code defines a new Angular component that renders a simple "About page" message.

2. Next, open up `app.component.ts` in the `src/app` directory and modify it to use dynamic component rendering with routes. Replace the contents of the file with the following code:

    ```typescript
      import { Component } from '@angular/core';

      @Component({
        selector: 'app-root',    
        template: `
        <nav>
          <a routerLink="/">Home</a>
          <a routerLink="/about">About</a>
        </nav>
        <router-outlet></router-outlet>`     
      })
      export class AppComponent {}
      ```

    This code defines the main app component that renders a navigation menu with links to the home and about pages. The `router-outlet` directive is used to dynamically render the appropriate component based on the current route.

3. Open up `app.module.ts` in the `src/app` directory and import the `RouterModule` and `Routes` classes from `@angular/router`. Then, define a new `Routes` array that maps URLs to components:

    ```typescript
    import { BrowserModule } from '@angular/platform-browser';
    import { NgModule } from '@angular/core';
    import { RouterModule, Routes } from '@angular/router';

    import { AppComponent } from './app.component';
    import { HelloWorldComponent } from './hello-world.component';
    import { AboutComponent } from './about.component';

    const routes: Routes = [
      { path: '', component: HelloWorldComponent },
      { path: 'about', component: AboutComponent }
    ];

    @NgModule({
      declarations: [
        AppComponent,
        HelloWorldComponent,
        AboutComponent
      ],
      imports: [
        BrowserModule,
        RouterModule.forRoot(routes)
      ],
      providers: [],
      bootstrap: [AppComponent]
    })
    export class AppModule {}
    ```

    This code defines a new `Routes` array with two routes: one for the home page (which maps to the `HelloWorldComponent`) and one for the about page (which maps to the `AboutComponent`). The `RouterModule.forRoot()` method is used to configure the router with these routes.

4. Save all of the files and refresh the page in your web browser. You should now see the navigation menu with links to the home and about pages. Clicking on the links should dynamically render the appropriate component without refreshing the page.

That's it! This basic Angular demo covers creating an Angular project with the CLI, statically rendering components, and using dynamic component rendering with routes. From here, you can continue to explore Angular's many features and build more complex applications.
# Cumulative for the  Hello Angular
</details>
