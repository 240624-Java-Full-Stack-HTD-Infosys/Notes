# Cumulative for the  Custom Pipes
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Angular custom pipes.
</details>
<details><summary>Description</summary>

# Description

- The pipes are used to transform data from one form to other.
- Angular has many default pipes. 
- Along with default pipes Angular has custom pipes to tranform data based on the requirements of the developer.

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

- When displaying user information in applications, only the initial letters of their first and last names are usually shown instead of their full name. The default pipes in Angular cannot be utilized to achieve this format for email addresses or names. However, it is possible to create custom pipes in Angular that can convert the data to the desired format.
</details>
<details><summary>Implementation</summary> 

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

- Default pipes in Angular are often sufficient to meet most requirements for transforming data, but in cases where these pipes do not provide the necessary functionality, custom pipes can be employed. Developers can use custom pipes to transform data in a way that meets specific requirements that fall outside the scope of default pipes.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
