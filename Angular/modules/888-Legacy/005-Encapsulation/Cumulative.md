# Cumulative for the  Encapsulation
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define View Encapsulation.
</details>
<details><summary>Description</summary>

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



</details>
<details><summary>Real World Application</summary>

# Real World Application

- Any front-end application uses CSS to style the application.
- Since Angular works on component-based architecture, a single Angular application contains many components.
- Each component is styled differently as per requirements by the developer.
- The title of the page can be bold and aligned in the centre, where as the navigation bar can be of different colors, and the licence info is placed at the end in small letters etc.
- All components are can be styled independently using view encapsulation.
</details>
<details><summary>Implementation</summary> 

# Implementation


The steps to be followed are:

- Two components named top and bottom are created.

```properties
ng generate component top
```

```properties
ng generate component bottom
```

- A div tag with an h1 tag and a paragraph tag with some information is added to the HTML files of both the components
- Now, add the top and bottom components to the app component html file.

top.component.html:

```html
<div class ="container">
    <H1>Top Component</H1>
    <p> This is a component at the top</p>
</div>
```
bottom.component.html:

```html
<div class ="container"> 
    <H1>Bottom Component</H1>
    <p> This is a component at the bottom</p>
</div>
```
app.component.html:

```html
<app-top></app-top>
<app-bottom></app-bottom>
```

HTML page:

![Top and Bootom Component](/modules_new/resources/ComponentsTopBottom.png)


- Global styles are added by using `styles.css`.

`styles.css`

```CSS
* {
    margin: 0;
    padding: auto;
    box-sizing: border-box;
}

.container {
    width: 100vw;
    height: 50vh;
    padding: 30px;
}
```

HTML page:

![Gloabl styles](/modules_new/resources/ComponentTopBottomStyles.png)

1. ### `ViewEncapsulation.Emulated`:

- Each component is styled individually

top.component.css:

```CSS
.container{
    background-color: orange;
    color: white;
}
```

bottom.component.css:

```CSS
.container{
    background-color: white;
    color: orange;
}
```

HTML image:

![Emulated View](/modules_new/resources/EmulatedView.png)

2. ### `ViewEncapsulation.None`: 

- Unlike emulated to define `ViewEncapsulation.None` encapsulation should be added and defined in the component.
- The `h3` tag is styled by changing the text color to black and the background color to  orangered

top.component.ts

```ts

import { Component, OnInit, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'app-top',
  templateUrl: './top.component.html',
  styleUrls: ['./top.component.css'],
  encapsulation: ViewEncapsulation.None
})
export class TopComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}
```

top.component.css

```css
.container{
    background-color: orange;
    color: white;
}

h1{
    color: black;
    background-color: orangered;
}
```
HTML page:

![ViewEncapsulation.None](/modules_new/resources/ViewEncapsulationNone.png)

- As `ViewEncapsulation.None` sets CSS styles to global, h3 in both top and bottom components changed.

3. ### `ViewEncapsulation.ShadowDom`:

- The `ViewEncapsulation.ShadowDom` is added to the top component.
- All the properties of global CSS are not applied on the top component since the CSS styles are enclosed under shadow DOM.

top.component.ts:
```ts

import { Component, OnInit, ViewEncapsulation } from '@angular/core';

@Component({
  selector: 'app-top',
  templateUrl: './top.component.html',
  styleUrls: ['./top.component.css'],
  encapsulation: ViewEncapsulation.ShadowDom
})
export class TopComponent implements OnInit {

  constructor() { }

  ngOnInit(): void {
  }

}
```

HTML page:
![Shadow Dom](/modules_new/resources/ShadowDom.png)




</details>
<details><summary>Summary</summary> 

# Summary

- View Encapsulation is an important feature of Angular, to encapsulate components CSS into components view.

Types of view encapsulation:

1. `ViewEncapuslation.Emulated`: default view, limits CSS styles scope to component level.
2. `ViewEncapuslation.None`: sets CSS styles scope to global.
3. `ViewEncapuslation.ShadowDom`: encloses CSS styles under shadow DOM. Global css styles are not applicable.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
