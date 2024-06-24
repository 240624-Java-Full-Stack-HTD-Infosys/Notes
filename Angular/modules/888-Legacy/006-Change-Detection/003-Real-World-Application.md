# Real World Application

- The process of change detection for every small change in the application makes an application slow.
- So many applications use onPush strategy.
- Angular applications have many components in a hierarchical structure.
- Like the change in user name will only affect the component that deals with the user details but not the product component or retailer component of an Angular e-commerce application.
- In such conditions, it is not necessary to run change detection for other components, so these components can be set to onPush.

