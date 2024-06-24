# Description

Change detection is the ability to detect changes in an Angular application. It makes sure that the angular view is in sync with the model. `ngDoCheck` is used to detect any change in an Angular application.

Angular runs change detection in the following conditions:

1. In events like click, submit and mouseover etc.
2. Asynchronous functions like interval, and set timer are executed.
3. API request is invoked.

In angular, every component has its change detection. When a change occurs in a component, the change detection is run from the root component of the DOM to the current component.

### Types Of Change Detection

1. Default strategy: DOM structure of change detection, where the very component has its change detector.
2. onPush strategy: change detection for a particular component is ignored.

When a component is set to onPush strategy the following methods can be implemented to manually detect the changes.

1. Mark for check
2. Detect Changes
3. Detach
4. Reattach


zone.js and ngZone handle the asynchronous changes in the Angular application.







