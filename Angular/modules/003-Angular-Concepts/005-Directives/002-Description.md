# Description

## Structural directives

Structural directives are used for adding, removing, or manipulating DOM elements. Structural directives start with an asterisk (*) followed by a directive name.  There are three built-in structural directives - `ngIf`, `ngFor` and `ngSwitch`.

### ngIf Directive

The `*ngIf` directive allows us to add or remove DOM Elements based upon the Boolean expression. It doesn't hide the elements, but generally adds or removes them physically from the DOM.

### ngFor Directive

 The `*ngFor` directive is used to repeat a part of the HTML template once per each item from an iterable list.

### ngSwitch Directive

The Angular *NgSwitch* has a set of cooperating directives: `NgSwitch`, `NgSwitchCase`, and `NgSwitchDefault`.

The syntax for `ngSwitch` Directive:

```html
<container_element [ngSwitch]="switch_expression">  
    <inner_element *ngSwitchCase="match-1">...</inner_element>  
    <inner_element *ngSwitchCase="match-2">...</inner_element>  
    <inner_element *ngSwitchCase="match-3">...</inner_element>  
    <inner_element *ngSwitchDefault>...</inner_element>  
</container_element>
``` 
NgSwitch* is an attribute directive that controls the behaviour of the other two switch structural directives - *NgSwitchCase* and *NgSwitchDefault*. That's why we write *NgSwitch* as `[ngSwitch]`, *NgSwitchCase* as `*ngSwitchCase`, and *NgSwitchDefault* as `*ngSwitchDefault`.

*NgSwitchCase* displays its element when its value matches the switch value. *NgSwitchDefault* displays its element when no sibling *NgSwitchCase* matches the switch value.

### `<ng-template>`  

Structural directives can work with the HTML5 `<ng-template>` element, which is designed to hold template code. 




