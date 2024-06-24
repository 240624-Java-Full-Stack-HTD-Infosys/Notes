# Description

- Classes, boolean, string, date and objects can be passed as dependencies.
- Angular DI provides the necessary APIs to make the dependency configuration flexible.

### Specifying a provider token

- If the service class is specified as the provider token, the default behaviour is for the injector to instantiate that class using the new operator.

```ts
providers : [dependency]
```

The complete code of the above code is:

```ts
[{ provide: dependency, useClass: dependency }]
```

This expanded provider configuration has two properties:

1. `provide` property holds the key to locating a dependency value and configuring the injector.
2. provider definition object: Tells the injector how the dependency value should be created. 

provider-definition keys:

1. `useClass`: Informs  Angular DI to instantiate a provided class when a dependency is injected.
2. `useExisting`: Allows to alias a token and reference any existing one.
3. `useFactory`: Allows defining a function that constructs a dependency.
4. `useValue`: Provides a static value that should be used as a dependency.

## InjectionToken for non-class dependencies

- `InjectionToken` object is chosen to provide a token for non-class dependencies.


