# Cumulative for the  Change Detection
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define change detection.


</details>
<details><summary>Description</summary>

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







</details>
<details><summary>Real World Application</summary>

# Real World Application

- The process of change detection for every small change in the application makes an application slow.
- So many applications use onPush strategy.
- Angular applications have many components in a hierarchical structure.
- Like the change in user name will only affect the component that deals with the user details but not the product component or retailer component of an Angular e-commerce application.
- In such conditions, it is not necessary to run change detection for other components, so these components can be set to onPush.

</details>
<details><summary>Implementation</summary> 

# Implementation

Normal component decleration

sample.component.ts

```ts
import {Component, OnInit, } from '@angular/core';


@Component({
  selector: 'app-content',
  templateUrl:'./sample.component.html' ,
  styleUrls: ['./sample.component.css'],

})
export class SampleComponent implements OnInit {

 title = "Sample";
  constructor() { }

  ngOnInit(): void {
  }

}
```

To set the component to onPush stratergy `changeDetection:ChangeDetectionStrategy.OnPush` is added.

```ts
import {ChangeDetectionStrategy, Component, OnInit, } from '@angular/core';


@Component({
  selector: 'app-content',
  templateUrl:'./sample.component.html' ,
  styleUrls: ['./sample.component.css'],
  changeDetection:ChangeDetectionStrategy.OnPush,

})
export class SampleComponent implements OnInit {

 title = "Sample";
  constructor() { }

  ngOnInit(): void {
  }

}
```
  
</details>
<details><summary>Summary</summary> 

# Summary

- View and Model in an Angular application are in sync due to the change detection process.
- Every component has its change detector and when a change occurs the change detection is done from the root component to the respective component.
- This process makes the application slow.
- This problem can be resolved by setting Angular change detection to onPush.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
