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
  