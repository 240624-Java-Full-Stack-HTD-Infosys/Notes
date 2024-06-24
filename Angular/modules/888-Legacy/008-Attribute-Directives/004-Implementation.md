# Implementation

### 1. ngClass Directive:
The CSS classes in the app.component.css file:

```css
.red { 
    background-color: red;
}
.size20 {
    font-size: 20px; 
    font-style: italic;
}
```

Using the [ngClass] directive in the app.template.html file, to add or remove CSS Classes on the element.

```html
<h3 [ngClass]="'red'"> Need your attention</h3>
<div [ngClass]="['red','size20']"> Red Background, Text with Size 20px  </div>
<div [ngClass]="{'red':false,'size20':true}">Text with Size 20px</div>
```

HTML page:

![ngClass](/modules_new/resources/ngClass.png)

### 2. ngStyle Directive:

app.component.html

```html
Enter the username: <input type = 'text' [(ngModel)] = 'name'>
<div [ngStyle]="{'background-color':username === 'Admin' ? 'green' : 'red' }"></<div>
```

HTML page:
 
 ![ngStyle](/modules_new/resources/ngStyles1.png)

HTML page:
![ngStyle](/modules_new/resources/ngStyles2.png)

 ### 3. Custom Directives:

 When the command `ng generate directive text` is run in the terminal.

 text.directive.ts

 ```ts
 import { Directive} from '@angular/core';

@Directive({
  selector: '[appText]'
})
export class TextDirective {
    //You can add custom styling of DOM Elements here...
    constructor() {
    
    }
}

```




