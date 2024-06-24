# Cumulative for the  Dynamic Components
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Dynamic Components.
</details>
<details><summary>Description</summary>

# Description

Loading components during runtime is called Dynamic component loading.

Procedure to load components dynamically

1. Creating and Anchor Directive: 

Before adding components, It is necessary to define an anchor point to tell Angular where to insert components.

2. Loading Components:

Using `<ng-template>` and the Anchor directive selector, you can inform Angular where to dynamically load components.

3. Resolving components:

Using an array of components or by conditions or user actions the components can be loaded dynamically.




</details>
<details><summary>Real World Application</summary>

# Real-world Application

- An application that displays adds is a perfect example of dynamic components.
- Every advertisement is a component that is loaded dynamically and a new component is loaded every few seconds.
</details>
<details><summary>Implementation</summary> 

# Implementation

- An example of displaying Ads every three seconds is considered.

1. Creating and Anchor Directive

A directive named AdDirective is created.

ad.directive.ts: 

```ts
import { Directive, ViewContainerRef } from '@angular/core';

@Directive({
  selector: '[adHost]',
})
export class AdDirective {
  constructor(public viewContainerRef: ViewContainerRef) { }
}
```

- AdDirective injects `ViewContainerRef` to gain access to the view container of the element that will host the dynamically added component.

2. Loading Components

A component named adBanner is created


ad-banner.component.ts template:

```ts
template: `
  <div class="ad-banner-example">
    <h3>Advertisements</h3>
    <ng-template adHost></ng-template>
  </div>
`
```

3. Resolving components

AdBannerComponent takes an array of AdItem objects as input, which ultimately comes from AdService. AdItem objects specify the type of component to load and any data to bind to the component.AdService returns the actual ads making up the ad campaign.

Passing an array of components to AdBannerComponent allows for a dynamic list of ads without static elements in the template.

With its getAds() method, AdBannerComponent cycles through the array of AdItems and loads a new component every 3 seconds by calling loadComponent().

ad-banner.component.ts

```ts
export class AdBannerComponent implements OnInit, OnDestroy {
  @Input() ads: AdItem[] = [];

  currentAdIndex = -1;

  @ViewChild(AdDirective, {static: true}) adHost!: AdDirective;
  interval: number|undefined;

  ngOnInit(): void {
    this.loadComponent();
    this.getAds();
  }

  ngOnDestroy() {
    clearInterval(this.interval);
  }

  loadComponent() {
    this.currentAdIndex = (this.currentAdIndex + 1) % this.ads.length;
    const adItem = this.ads[this.currentAdIndex];

    const viewContainerRef = this.adHost.viewContainerRef;
    viewContainerRef.clear();

    const componentRef = viewContainerRef.createComponent<AdComponent>(adItem.component);
    componentRef.instance.data = adItem.data;
  }

  getAds() {
    this.interval = setInterval(() => {
      this.loadComponent();
    }, 3000);
  }
}
```



</details>
<details><summary>Summary</summary> 

# Summary

- The process of loading components on runtime at a particular interval or based on user actions is called dynamic component loading.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
