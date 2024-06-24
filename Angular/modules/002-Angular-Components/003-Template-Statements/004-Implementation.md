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