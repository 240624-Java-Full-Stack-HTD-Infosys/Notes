# Description

## Routing

In Single Page Applications, only one page is requested from the server, and it provides multiple views dynamically rather than loading the new pages from the server. 

The Router mechanism in Angular provides a way to navigate from one view to another view in the application.

Angular provides a `RouterModule` that has the necessary service providers and directives for navigating through application views. The **router** defines the navigation of views on a single page and interprets URL links to determine which views to create or destroy, and which components to load or unload. 
A **routing component** imports the Router module, and its template contains a `RouterOutlet` element where it can display views produced by the router.