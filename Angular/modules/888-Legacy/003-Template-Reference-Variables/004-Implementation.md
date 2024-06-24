# Implementation

creating input and disabling the submit button if it is empty.

```html
<input type="text" #inputText ngModel value="enter text">
<button [disabled]="inputText.value.length===0">Submit</button>
```

- In the above code `#inputText` is the template reference variable.
- ngModel is included to access and alter the `[disabled]` property.
- `.value` is used to get the value of the template reference variable.
- `.length` is used to get the length of the value. If the length of the value is zero, the text field is empty and the submit button is disabled.

