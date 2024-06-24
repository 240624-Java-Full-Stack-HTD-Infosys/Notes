# Description

**Attribute Directives**

Attribute Directives are used to modify the properties of DOM.

Examples of Attribute Directives:

1. `ngClass`
2. `ngStyle`
3. `ngModel`

A custom attribute directive can be created by creating a directive as below.

```properties
ng generate directive <directive name>
```

### ngClass Directive

The `[ngClass]` directive is used for adding or removing the CSS classes on an HTML element. It allows us to apply CSS classes dynamically based on expression evaluation. 

**Syntax:** `<some-element [ngClass]="value"> ....</some-element>`

The value can be:
-  **string** - the CSS classes declared as string. For example, `<some-element [ngClass]="'first second'">...</some-element>` where `first` and `second` are the two CSS Classes delimited by space. Both the `first` and `second` CSS styles will be applied to the element.

- **Array** - the CSS classes declared as Array elements. For example,`<some-element [ngClass]="['first', 'second']">...</some-element>` .

- **Object** - in which *keys* are CSS classes and *values* are expression that  evaluates true or false.  The CSS Class is applied to the element when the expression evaluates a truthy value, else they will be removed. For example,`<some-element [ngClass]="{'first': true, 'second': true, 'third': false}">...</some-element>`.

### ngStyle Directive

The `[ngStyle]` directive allows us to dynamically change the style of the HTML element based on the expression.

**Syntax:** `<some-element [ngStyle]="objExp">...</some-element>`

### Custom Directives

We can create our custom directives to use in the Angular component with the CLI command `ng generate directive <name of the directive>`.

**For example**, When we run this command `ng generate directive text` in a terminal, the CLI creates a *text.directive.ts* file and corresponding test file *text.directive.spec.ts* under *src/app* folder in our application. Also, CLI declares this directive class under *AppModule*.





