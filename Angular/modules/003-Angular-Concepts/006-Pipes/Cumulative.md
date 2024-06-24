# Cumulative for the  Pipes
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Angular pipes.
- To define different types of pipes.
</details>
<details><summary>Description</summary>

# Description

## Pipes

In many full stack applications the data is received from the backend in HTTP messages and formatted in JSON or XML (or similar). When that data is displayed on the HTML page the data will need to be more human readable. Pipes are used to transform data from one form to another.

Pipes are classified into two types.

1. Default Pipes
2. Custom Pipes

## Default Pipes
Data, currency, case and percent are a few commonly used default pipes.

The syntax for pipe is:

```html
{{ text | pipe_name }}
```
where `{{}}` represent the Text interpolation and `|` is the syntax for the pipe.

## Custom Pipes
The syntax to create a custom pipe is:

```properties
ng generate pipe <pipe-name>
```

The syntax for custom pipe is:

```html
{{Text | <pipe-name>}}
```
</details>
<details><summary>Real World Application</summary>

# Real World Application

- Date received from the backend can not be displayed on a web page, because it is not in a readable format. The date is converted into a specific format like MM-DD-YYYY, using the `date` Pipe.
- The price of a product received from the backend is a number. The currency symbol should be added to the price while displaying the price on a website. `currency` pipe converts adds the currency symbol to the number.
- Sometimes, conversion of text from lowercase to uppercase or to title case is necessary. `lowercase`, `uppercase`, and `titlecase` pipes convert text to their respective form.
</details>
<details><summary>Implementation</summary> 

# Implementation
### Default Pipes
app.component.ts:

```ts
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: 'app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  
  title = "Template literal works!";
  userName = "taylor.swift@xyz.com"
  today = new Date();
  price = 444;
  
}
```

The data in component files

1. title
2. user name
3. date 
4. price

app.component.html:

```html
<p>Date : {{ today | date:"MM-dd-YYYY"}}</p>
<p>Price : {{price | currency:"INR"}}</p>
<p>lower case : {{title | lowercase}}</p>
<p>upper case: {{title | uppercase}}</p>
<p>title case: {{title | titlecase}}</p>
<p>custom pipe: {{userName | user | uppercase}}</p>
```

<i>**Note:** Detailed explanation and implementation of custom pipes is given in upcoming topics.</i>

HTML line 1: Date is transformed to MM-dd-YYYY format using `date` pipe.<br>
HTML line 2: Price is represented in Indian Rupees using the `currency` pipe.<br>
HTML line 3: Text is transformed to lowercase using the `lowercase` pipe.<br>
HTML line 4: Text is transformed to upper case using the `uppercase` pipe.<br>
HTML line 5: Text is transformed to title case using `titlecase` pipe.<br>
HTML line 6: A email is transformed to a format with first letters of the first name and last name using a custom pipe named user.<br>


HTML page:

![Pipes](/modules/resources/Pipes.PNG)

### Custom Pipes
# Implementation

Custom pipe user is created with the below command

```properties
ng generate pipe user
```
app.component.ts:

```ts
import { Component } from '@angular/core';


@Component({
  selector: 'app-root',
  templateUrl: 'app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  userName = "taylor.swift@xyz.com"
}
```

user.pipe.ts:

```ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'user'
})
export class UserPipe implements PipeTransform {

  transform(value: string, ...args: any[]): string {
    let values= value.split(".");
    return values[0][0]+values[1][0];
  }

}
```

- Generally, the official email is in the format of firstname.lastname@company.com.
- The "." is used to split the email and store it in an array.
- The first letter of two words is taken.
- As email is not case sensitive, it's represented in lowercase. In the HTML file, along with the custom pipe "user", an uppercase pipe is used to format the letters.

The HTML code is as following:

```html
<p>custom pipe: {{userName | user | uppercase}}</p>
```

This displays:  
  
`custom pipe: TS`
</details>
<details><summary>Summary</summary> 

# Summary

- Angular pipes are used to transform data from one form to other. 
- `date`, `lowercase`, `uppercase`, `percentage`, `titlecase`, `currency` and `percentage` are examples for inbuilt pipes. 
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
