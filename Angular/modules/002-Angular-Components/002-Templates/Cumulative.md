# Cumulative for the  Templates
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Template.
</details>
<details><summary>Description</summary>

# Description

## Template
- Template is a blueprint for a part of the user interface(UI).
- Templates can be considered HTML documents, as they are written in HTML.
- A special syntax can be used in templates to add additional functionality. this is an improvement over the normal HTML page.
- As Angular template is only a part of UI, some tags like `<html>`,`<body>` are not included in templates.
- Angular template is directly related to the component view.
</details>
<details><summary>Real World Application</summary>

# Real World Application

- Every web application has an HTML template. Angular components need a template to create a UI.
- All the components in a web page, like title, search, products, and text are part of the HTML template.

</details>
<details><summary>Implementation</summary> 

# Implementation

1. Inline Template

- Inline templates are enclosed in backtick(`)

app.component.ts:

``` ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `<H1> App Component</H1>
  <p>This is an Inline Template</p>`,
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'sample';
}
```
- In the above component `template` is used and the HTML code is enclosed in backtick(`).


- The angular page looks like this:

![html page](/modules_new/resources/Inline%20tempate.PNG)


1. External Template

- `templateUrl` is used to add an external HTML template.

app.component.ts:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'sample';
}

```

app.component.html:

```html
<h1>Angular Template</h1>
<p> This is a Template url</p>
```

- The angular page looks like this:

![html page](/modules_new/resources/Templateurl.PNG)

</details>
<details><summary>Summary</summary> 

# Summary

- Angular template is the blueprint of the user interface.
- `template` and `templateUrl` is used to add the template to an angular component.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
