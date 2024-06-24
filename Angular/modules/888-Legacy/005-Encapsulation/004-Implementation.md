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




