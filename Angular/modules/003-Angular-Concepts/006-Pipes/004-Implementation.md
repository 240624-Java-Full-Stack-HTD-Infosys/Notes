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
