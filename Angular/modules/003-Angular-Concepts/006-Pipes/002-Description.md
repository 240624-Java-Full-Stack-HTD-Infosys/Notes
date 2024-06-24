# Description

## Pipes

In many full stack applications the data is received from the backend in HTTP messages and formatted in JSON or XML (or similar). When that data is displayed on the HTML page the data will need to be more human readable. Pipes are used to transform data from one form to another.

Pipes are classified into two types.

1. Default Pipes
2. Custom Pipes

## Default Pipes
Data, currency, case and percent are a few commonly used default pipes.

The syntax for pipe is:

```html
{{ text | pipe_name }}
```
where `{{}}` represent the Text interpolation and `|` is the syntax for the pipe.

## Custom Pipes
The syntax to create a custom pipe is:

```properties
ng generate pipe <pipe-name>
```

The syntax for custom pipe is:

```html
{{Text | <pipe-name>}}
```
