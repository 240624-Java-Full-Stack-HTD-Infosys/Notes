# Cumulative for the  Template Reference Variables
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define template reference variables.


</details>
<details><summary>Description</summary>

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
</details>
<details><summary>Real World Application</summary>

# Real World Application

- Template reference variables can be used to get data from input fields in an Html page.
- Based on the input the dom elements can be modified.
- A good example is disabling the submit button if the input field is empty.
</details>
<details><summary>Implementation</summary> 

# Implementation

creating input and disabling the submit button if it is empty.

```html
<input type="text" #inputText ngModel value="enter text">
<button [disabled]="inputText.value.length===0">Submit</button>
```

- In the above code `#inputText` is the template reference variable.
- ngModel is included to access and alter the `[disabled]` property.
- `.value` is used to get the value of the template reference variable.
- `.length` is used to get the length of the value. If the length of the value is zero, the text field is empty and the submit button is disabled.

</details>
<details><summary>Summary</summary> 

# Summary

- Template reference variables are used to access all the properties of an element in DOM.
- The syntax of the template reference variable is `#Template-reference-variable`.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
