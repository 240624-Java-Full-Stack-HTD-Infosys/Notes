# Description

**Service** : A TypeScript class to share data or functionality throughout the application.

Uses of service:

- Code reuse
- Cross-component communication

**Dependency injection**: A coding pattern in which a class receives the instances of the objects it needs (called dependencies) from an external source rather than creating them itself.

A service can be created and injected in the following steps:

1. Create a class and decorate it with the @Injectable decorator and export it.

1. Register the provider => a provider is a code that can create or return a service 
    - We can add the service to the provider's property in either:
      - @Component => Injectable to component and its children. 
      - @NgModule => Injectable everywhere in an application .
2. Inject the Service
    - We achieve dependency injection in the constructor of the class in which we wish to use the service. 
    - Similar to Java, every class has an implicit no-arg constructor if no other constructor is defined.
    - To inject dependencies, we need an explicit constructor passing in the service to be injected. 

 ```ts
    export class MyComponent {
                constructor(private myService: MyService) {}
            }
```

        
            




