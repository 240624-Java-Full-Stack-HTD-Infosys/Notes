# Description

### Directives

 A Directive is a custom HTML element or attribute used to power up and extend our HTML 

- Directives fall into one of three categories
    - Component Directive: established in the selector attribute of the @Component decorator 
    - Structural Directive: changes the structure or layout of a view by manipulating, adding, or removing elements and their children 
        - `*ngIf`: takes a boolean expression and makes an entire chunk of the DOM appear or disappear (exposed in BrowserModule)
        - `*ngFor`: used to create for loops, at minimum needs a looping variable and a list (exposed in BrowserModule)
        - `ngSwitch` : (actually a set of directives and ngSwitch is an attribute directive since it controls the behaviour of *ngSwitchCase and *ngSwitchDefault)
            - ngSwitch
            - *ngSwitchCase
            - *ngSwitchDefault
    - Attribute Directive: listens to and modifies the behaviour of other elements, attributes, properties, and components. However, usually applied to attributes 
        - NgClass : adds and removes a set of CSS classes 
        - NgStyle : adds and removes a set of HTML styles
        - NgModel : allows for two-way data binding to an HTML form element (exposed in FormsModule)

### Differences between Directives and Components

In a short note, A component(@component) is a directive-with-a-template.

- Some of the major differences are mentioned in a tabular form

    | Component | Directive |
    |---- | ---------
    | To register a component we use @Component meta-data annotation  | To register directives we use @Directive meta-data annotation |
    | Components are typically used to create UI widgets| Directive is used to add behaviour to an existing DOM element |
    | Component is used to break up the application into smaller components| Directive is used to design re-usable components|
    | Only one component can be present per DOM element | Many directives can be used per DOM element |
    | @View decorator or templateurl/template are mandatory | Directive doesn't use View|



<br>
<i> <b>Note</b>: detailed explanation about attribute directives and structural directives will be given in the upcoming modules.</i> 
