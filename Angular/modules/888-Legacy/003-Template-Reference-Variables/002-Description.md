# Description

- Template variables are also called local reference variables.
- Template reference variables help to access all the properties of any element inside the DOM.
- Tasks such as responding to user input or finely tuning the application forms are done by template variables.

A template variable can refer to:

1. DOM element within the template
2. Directive
3. Component
4. TemplateRef from an ng-template
5. Web component


- Any HTML element can be accessed using the template reference variable with the below syntax.

```html
<tag #template_reference_variable></tag>
```

- Template reference variables can not be accessed directly in the TypeScript file.
- A reference is passed explicitly through an event to achieve it.