# Implementation


## User-Defined Directive

Consider my highlight directive which highlights the text on the HTML page, when the user hovers the mouse on the text.

A directive named Highlight is created by running the below line in the terminal.

```properties
ng generate directive highlight
```

highlight.directive.ts

```ts
import { Directive, HostListener, ElementRef } from '@angular/core';

@Directive({
  selector: '[appHighlight]'
})
export class HighlightDirective {

  constructor(private e: ElementRef) {  
  }  

  @HostListener('mouseover') onMouseOver() {  
    this.changeBackgroundColor('blue');  
  }

  @HostListener('mouseleave') onMouseLeave() {  
    this.changeBackgroundColor('white');  
  }  

  private changeBackgroundColor(color: string) {  
    this.e.nativeElement.style.backgroundColor = color;  

  }    

}
```

app.component.html:

```html
<p appHighlight>Highlight me!</p>
```

HTML page:

![Highlight Directive](/modules_new/resources/highlight1.png)

The HTML page on mouse hover:

![Highlight Directive on mouse hover](/modules_new/resources/highlight2.png)


# Built-in Directive

Angular has many built-in directives. Unlike the user define directives the implementation for the built-in directives is predefined in Angular.

Consider two `div` tags with a built-in structural directive `*ngIf`.

app.component.html:

```html
<div *ngIf= "true" >  
    Condition is true!
    </div>  
<div *ngIf="false">
    Condition is False!
</div>
```

The statement in `div` block with the condition true will be in DOM. 

HTML page:

![Built-in Directive](/modules_new/resources/Built-in_Directive.png)


<i> <b>Note</b>: Explanation and implementation for attribute directives and structural directives will be given in the upcoming modules.</i> 