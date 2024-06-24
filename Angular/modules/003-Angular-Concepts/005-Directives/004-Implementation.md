# Implementation

### 1. ngIf:

The paragraph with `*ngIf` condition true is displayed.

```html
<p *ngIf="true">
  The expression is true, this paragraph is in DOM.
</p>
<p *ngIf="false">
  Expression is false, this paragraph is not in DOM.
</p>
```

HTML page:

![ngIf](/modules_new/resources/ngIf-1.png)


We can also have an else block associated with a *ngIf directive.

If the `*ngIf` condition is false the elseBlock is implmented.

```html
<div *ngIf="5>10 else elseBlock">  
5 is greater than 10...
</div>  
<ng-template #elseBlock>  
10 is greater than 5... 
</ng-template> 
```

HTML page:

![ngIf](/modules_new/resources/ngIf-2.png)

### 2. ngFor:

The `*ngFor` is used to iterate through the customer object instances.

app.component.ts

```ts
import { Component } from '@angular/core';

@Component({
 selector: 'app-root',
 templateUrl: './app.component.html',
 styleUrls: ['./app.component.css']
})
export class AppComponent {
 customers : Customer[] = [
   {id : 234 , name: 'John'},
   {id : 235 , name: 'Adam'},
   {id : 236 , name: 'Nick'}
 ];
}
class Customer { 
 id:number;
 name: string;
} 
```

app.component.html
```html
<table>
<tr *ngFor="let customer of customers;">
    <td>{{customer.id}}</td>
    <td>{{customer.name}}</td>   
</tr>
</table>
```

HTML page:

![ngFor](/modules_new/resources/ngForExample.png)


### 3. switch:

The `*ngSwitch` has different cases. If any case is satisfied, the statement in `div` tag associated with that case is displayed.

app.component.html

```html
<div class = 'input-num'>
Enter the number<input type='text' [(ngModel)]="num" />
</div>
<div [ngSwitch]="num">
  <div *ngSwitchCase="'1'">You entered - One</div>
  <div *ngSwitchCase="'2'">You entered - Two</div>
  <div *ngSwitchCase="'3'">You entered - Three</div>
  <div *ngSwitchCase="'4'">You entered - Four</div>
  <div *ngSwitchCase="'5'">You entered - Five</div>
  <div *ngSwitchDefault> ...default </div>
</div>
```

- Declare num in app.component.ts.

```ts
import { Component } from '@angular/core';

@Component({
 selector: 'app-root',
 templateUrl: './app.component.html',
 styleUrls: ['./app.component.css']
})
export class AppComponent {
num =0;
}
```

HTML page:

![ngSwitch](/modules_new/resources/ngSwitch-1.png)

![ngSwitch](/modules_new/resources/ngSwitch-2.png)





