# Description

- To download or upload data and access other back-end services, most front-end applications must communicate with a server using the HTTP protocol. The HttpClient is a lightweight, easy-to-use, and robust HTTP client library. It allows developers to collect external data and post, get etc.

- The `HttpClient` Module is already included when creating a new Angular app. We just need to register it in our Angular application. In `src/app/app.module.ts` file, import the *HttpClient* module to make use of the *HttpClient* service.

```typescript
import { HttpClient }    from '@angular/common/http';
```
Also, include the HttpClientModule in `@NgModule`'s imports array.
```typescript
@NgModule({
  imports: [
    BrowserModule,
    HttpClient
   ]
})
```