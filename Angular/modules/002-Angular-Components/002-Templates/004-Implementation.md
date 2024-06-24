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

