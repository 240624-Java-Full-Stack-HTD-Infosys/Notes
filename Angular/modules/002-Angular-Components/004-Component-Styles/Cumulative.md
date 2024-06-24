# Cumulative for the  Component Styles
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Component Styles.
</details>
<details><summary>Description</summary>

# Description

Angular applications can be styled using standard CSS. CSS stylesheets, selectors, rules and media queries can be directly added to an Angular application.

Ways to add styles to a component:

1. `styles` or `styleUrls` metadata
2. Inline in the template HTML
3. CSS imports
</details>
<details><summary>Real World Application</summary>

# Real World Application

Angular uses CSS to style and lay out web pages.

Applications of component styles include altering font, colour, size, spacing of the content, splitting into multiple columns, adding animations etc.
</details>
<details><summary>Implementation</summary> 

# Implementation

1. styles:

- Angular CLI code to create a component with empty styles.


```properties
ng generate component component-name --inline-style
```

- The colour of the paragraph is set to red using styles.


app.component.ts

```ts
import { Component } from '@angular/core';


@Component({
  selector: 'app-root',
  template: `<h1>App Component</h1>
  <p>Styles is working<p>`,
  styles: ['p { color: red,}']
})
export class AppComponent {
  color='white';
  title = "Sample";
  highlight color(newColor: string):void{
    this.color=newColor

  } 
}
```

HTML page:

![styles](/modules_new/resources/styles.png)


1. `stylesUrls`: An URL to the CSS style sheet can be added using `stylesUrls`.


app.component.ts:

```ts
import { Component } from '@angular/core';


@Component({
  selector: 'app-root',
  template: `<h1>App Component</h1>
  <p>styleUrls is working</p>`,
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  color='white';
  title = "Sample";
  highlightColor(newColor: string):void{
    this.color=newColor

  } 
}
```

app.component.css:

```css
h1{
    margin-bottom: 10px;
    color: orange;
}
```

HTML page:

![StyleUrls](/modules_new/resources/stylesUrls.png)

3. Inline in the template HTML:



app.component.ts:

```ts
import { Component } from '@angular/core';


@Component({
  selector: 'app-root',
  template: `<h1>App Component</h1>
  <p>Inline Styles is working</p>
  <style>
      p {
        background-color: orange;
        color: white;
        margin-top: 10px ;
      }
    </style>`,
})
export class AppComponent {
  color='white';
  title = "Sample";
  highlightColor(newColor: string):void{
    this.color=newColor

  } 
}
```

4. CSS imports

- An external CSS file named componentstyles is created.
- A link to the CSS page is added to the component.

```css
p{
    color: orange;
    margin-top: 10px;
}
```

app.component.ts

```ts
import { Component } from '@angular/core';


@Component({
  selector: 'app-root',
  template: `<h1>App Component</h1>
  <p>External link is working</p>
  <link rel="stylesheet" href="componentstyles.css">`,
})
export class AppComponent {
  color='white';
  title = "Sample";
  highlightColor(newColor: string):void{
    this.color=newColor

  }
}
```

HTML page:

![External CSS](/modules_new/resources/ExtenalCSS.png)



</details>
<details><summary>Summary</summary> 

# Summary

- CSS styles are used to style the web pages.
- Angular components are styled using CSS by `styles`, `styleUrls`, inline CSS in template and CSS imports.
- `styleUrls` is most commonly used.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
