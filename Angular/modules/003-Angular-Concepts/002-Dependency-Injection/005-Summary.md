# Summary

- Dependency injection is a programming pattern where a class receives the necessary objects or dependencies from an external source instead of creating them itself
- There are several ways to provide and inject dependencies in Angular
   - `providers` array at the component, module, or application level
   - `providedIn` property of `@Injectable`
   - `providers` array in the `ApplicationConfig` object passed to `bootstrapApplication()`
