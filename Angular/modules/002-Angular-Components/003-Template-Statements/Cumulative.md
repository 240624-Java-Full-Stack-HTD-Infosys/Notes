# Cumulative for the  Template Statements
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Template Statements.
</details>
<details><summary>Description</summary>

# Description

- Template Statements are methods or properties, used in HTML invoked in response to user events.

**Syntax**

- Template statements use a language similar to javascript but the parser for template statements is not similar to template expressions.
  
The following JavaScript and template expression syntax is not allowed in Template statements.

- New Increment and decrement operators, ++ and --
- Operator assignment, such as += and -=
- The bitwise operators, such as & and The pipe operator |.

</details>
<details><summary>Real World Application</summary>

# Real World Application


- Submitting data after the submit button is clicked can be implemented using Template statements.
- Incrementing or decrementing the value of a number like the quantity of a product.
</details>
<details><summary>Implementation</summary> 

# Implamentation

- Consider a text which dynamically displays, how many times a specific button is clicked.

app.component.html:

```html
<button (click) = 'countClicks();'> click me!</button>
<p>No of clicks : {{count}}</p>
```

- In the above code, every time a button is clicked the method countClicks() is implemented.
- text interpolation is implemented with a variable click.

app.component.ts:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: 'app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  title = 'sample';
  count =0;
  countClicks():void{
    this.count+=1;

  }
}

```

- In the above code, the method countClicks() increments the count every time the button is clicked.

Html page:

![Before Click](/modules_new/resources/stringinterpolation1.PNG)

- After the button is clicked, the text is updated to 1.

![After Click](/modules_new/resources/stringinterpolation2.PNG)

- By using template statement and text Interpolation, the data from the TypeScript class to HTML page is dynamically updated. 
</details>
<details><summary>Summary</summary> 

# Summary

- Template statements are used to monitor and respond to user actions, like key strokes, clicks etc.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
