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