# Description
## View Encapsulation

View Encapsulation is a behaviour in Angular, where component CSS styles are encapsulated into the component's view.

## Types of View Encapsulation

1. `ViewEncapuslation.Emulated`:
   - Angular modifies the component CSS selectors so that it is only applied to the component's view and doesn't affect other parts of the application.
   - `ViewEncapuslation.Emulated` is implemented by default in Angular.
2. `ViewEncapsulation.None`: 
   - Angular does not apply any sort of view encapsulation and the styles are added to the `<head>` so any styles specified in a component are globally applied.

3. `ViewEncapsulation.ShadowDom`: 
   - Angular uses Shadow DOM Api to enclose the component's view into a ShadowRoot.
   - The CSS styles of a component only affect elements within the respective component's view.
   - All the styles are applied in an isolated manner.
   - Not all browsers support `ViewEncapsulation.ShadowDom`.



