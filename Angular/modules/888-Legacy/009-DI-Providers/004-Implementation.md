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

