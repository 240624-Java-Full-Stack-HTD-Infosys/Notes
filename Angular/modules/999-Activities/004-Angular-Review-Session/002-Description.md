# Angular: ANG-REVIEW-ANG

### Contributors

Author: Jonathan De La Cruz

Reviewers:

## Scope

This review session will cover the entire Angular unit. Modules covered are as follows. 

## Conducting Review Session

**Estimated Time:** 120 minutes

### Review Handout

[Angular-Review-Handout.md]([Angular-Review-Handout.md](https://revature0.sharepoint.com/:t:/s/trainers/EQmARjKCRGFNtuvPXe-4M8gBxWYueEMbgM_3AA7YkB6CMA?e=e5w2W0))

## Review Session Information

### 001-Angular Orientation

#### Define

- Angular - A front-end web framework for creating single page apps. 
- Single Page Application - A type of web application that loads a single HTML page and dynamically updates that page as the user interacts with it, without requiring the page to be reloaded
- Webpack - A module bundler for JavaScript apps, it's used to package and optimize an app's code and resources into a single bundle that can be served to the user in a web browser. 

#### Importance/Use Case

- Environment Set up - we want the associates to have all programs, libraries and tooling required to work with Angular applications installed on their machines. 
- Understanding single page web applications is core to the rest of the unit - we want them to leverage the strengths of SPAs and not attempt to develop traditional sites while fighting the framework. 

#### Common Pitfalls

1. Confusing Angular and AngularJS (following incorrect tutorials or Stack Overflow posts.)

#### Interview Questions

1. What is a Single Page Application, how does it differ from a traditional website? What are the pros and cons?
2. What is the command to initialize a new Angular application?
3. How is Angular different from AngularJS?


### 002-Angular Foundation

#### Define

- Component - a building block of the user interface that encapsulates a set of related functionality and presents a view to the user. Consists of multiple parts. 
- Decorator - A special declaration that can be attached to a class declaration, method, property, or parameter; used to modify their behavior or add additional meta data that can be used by other parts of the app. 
- Template - HTML file in a component that defines how the component is rendered in the application, contains special syntax and directives to support data binding, event handline, and other features. 
- 1-way data binding - Data binding that flows from the component to the view. 
- 2-way data binding - Data binding where data can flow in either direction, mainly used to create forms. 
- Structural directive - A type of directive that is used to modify the structure of the HTML document, by adding, removing, or manipulating elements based on a condition or data set.
- Attribute directive - A type of directive that is used to modify the behavior or appearance of an HTML element, by applying a set of instructions or styles to it.

#### Importance/Use Case

- This module introduces essential concepts and syntax such as modules, components, templates, data binding, and directives that form the foundation of building Angular applications.

#### Common Pitfalls

1. Overwhelmed by the Angular project structure. 
2. Package.json vs package-lock.json and node_modules.json. 

#### Interview Questions

1. What is directive?
2. What is the purpose of decorator?
3. What are different ways to data bind? 
4. What is event binding?


### 003-Angular Pipes

#### Define

- Pipe - A feature that allows developers to transform the value of an expression or variable into a desired output format, by applying a set of instructions or filters to it.

#### Importance/Use Case

- Teaches associates how to transform and manipulate data in Angular applications using built-in and custom pipes, which is a crucial aspect of building efficient and dynamic applications.

#### Common Pitfalls

1. Not knowing what a pipe is or when to use them. 

#### Interview Questions

1. What is a pipe? When would you use one?
2. How can you create a custom pipe?


### 004-Angular Component Depth

#### Define

- Component lifecycle - Creation, Initialization, View Creation, Content Checking, Destruction
- Event Emitter - A mechanism used to emit custom events from a component to its parent or other components in the application.

#### Importance/Use Case

- Teaches associates how to style components within an Angular application. 
- Component lifecycle and associated lifecycle hooks are essential for creating a dynamic application. 
 
#### Common Pitfalls

1. When creating a component, associates need to ensure that the new component is inside a declaration array in @NgModule decorator. They also need to ensure that they have imported the typescript class of the component where the NgModule is. 

#### Interview Questions

1. How do we share data between components? 
2. What is component?
3. How is a component different from a service?
4. What are lifecycle hooks? Give 2 examples


### 005-Angular Routing and Services

#### Define

- Routing - The process of defining the navigation paths and views for an application, and handling navigation between those paths and views.
- Route Guard - Used to control access to routes in an application based on various criteria, such as user authentication, user roles, or other conditions.
- Services - A class that provides functionality to other parts of the application. Services are typically used to provide shared data, business logic, or utilities that are used across multiple components.
- Dependency Injection - A design pattern that allows a component to request dependencies from an external source, rather than creating or managing them itself. Used to inject services into components or other areas of an Angular application that requires their functionality. 

#### Importance/Use Case

- Routing is how we navigate through an SPA, without an understanding of routing within Angular associates cannot leverage the advantages of an SPA versus a traditional web page. 
- Route Guards add security and prevent unwanted access to certain routes, components, and the data within them. Essential to writing a secure application.

#### Common Pitfalls

1. RouterOutlet needs to be where they want the routing components to be shown.
2. Not using Angular routing specific navigation tools like RouterLink versus hrefs (which cause refreshes.)

#### Interview Questions

1. Describe Dependency Injection design pattern and how angular handles it?
2. What are services?
3. (T/F) Changing the route via Angular Routing will send an http call


### 006-Angular with RxJS and Http

#### Define

- RxJS - A library that provides reactive programming features, such as observables and operators, to make it easier to work with asynchronous data streams.
- HttpClient - a built-in Angular service for making HTTP requests to a server or external API.
- Pub/Sub design pattern - The publish/subscribe design pattern used in Angular, allowing components to communicate without having to know about each other directly. 
- Observable - An observable can be thought of as a stream of values that can be observed over time. We can use operators to transform the data stream and subscribe to the observable to receive updates as new data is emitted.
- Subjects - A type of Observable that allows for multicasting, which means that it can send the same data stream to multiple subscribers.

#### Importance/Use Case

- HttpClient is the main way associates will consume content from their back-end or an outside API. 
- Associates need to understand RxJS observables and subjects to pass data from one part of their application to another asynchronously. 

#### Common Pitfalls

1.  Not understanding how to work with observables. 
2. Understanding the asynchronous nature of observables. 

#### Interview Questions

1. How do we make http calls in angular?
2. How is an observable different from a promise?

# Cumulative for the  Angular Review Session
