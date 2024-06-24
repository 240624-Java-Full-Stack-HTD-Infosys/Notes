# Cumulative for the  DI Providers
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Dependency Injection Providers.


</details>
<details><summary>Description</summary>

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


</details>
<details><summary>Real World Application</summary>

# Real World Application

- Consider an application with different message services like MessageService, ErrorMessageService and DirectMessageService.
- A single dependency can not be provided in all cases.
- Normally MessageService is the default option but if an error message is to be sent, the dependency should be changed to ErrorMessageService.
- If the user sets DirectMessage as default the condition should be checked and DirectMessage dependency should be provided.
- All the above requirements can be achieved using Dependency Providers.
</details>
<details><summary>Implementation</summary> 

# Implementation

Consider a provider syntax with MessageService dependency

```ts
 providers: [MessageService]
```

The expanded syntax is:

```ts
 providers: [{ provide: MessageService, useClass: MessageService }
]
```

1. useClass: To pass a different class instead of the same class useClass can be used.

DirectMessageService is used instead of MessageService.

```ts
  [{ provide: MessageService, useClass: DirectMessageService }]
```

- To use a class different from a token but that class is already used as a provider.

```ts
Providers: [ ErrorMessageService, { provide: MessageService, useClass: ErrorMessageService}]
```
- In the above case, the injector will create two different instances of ErrorMessageService class.
- This problem can be solved using `useExisting`.

2. useExisting

```ts
Providers: [ ErrorMessageService, { provide: MessageService, useExisting: ErrorMessageService}]
```

- Sometimes a readymade object is required rather than asking for the injector to create it from a class.
- To inject a created object `useValue` is used.

3. `useValue`

```ts
const messageObj = {
messageType: ‘Direct’,
messageText: ‘this is a direct message’
};
Providers: [{ provide: MessageService, useValue: messageObj }]
```

4. Injection Token:

- To generate a unique value for every instance to avoid the same token conflits InjectionToken is used.

```ts
import { ReflectiveInjector } from '@angular/core';
class DirectMessageService {};
class ErrorMessageService {};
let Message Token = "DMService";
let Message Token = "EMService";
let injector = ReflectiveInjector.resolveAndCreate([
{ provide: MessageToken, useClass: DirectMessageService },
{ provide: MessageToken, useClass: ErrorMessageService },
]);
```

5. Factory Providers:

- To create dependency values dynamically using the runtime values factory provider is used.

For example, if the user allows DirectMessage in the settings DirectMessage is provided as a dependency.

```ts
let message factory = (settings) => {
    if(settings.DirectEnabled)
      return new DirectMessage();
};
```

```ts
{ provide: DirectMessageService, useFactory: messageFactory};
```

</details>
<details><summary>Summary</summary> 

# Summary

- Dependencies can be classes, strings, boolean and date.
- To make dependency injection more flexible dependency injection providers are used.
- useClass, useValue, useExisting and useFactory properties are used based on the requirement of the developer.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
