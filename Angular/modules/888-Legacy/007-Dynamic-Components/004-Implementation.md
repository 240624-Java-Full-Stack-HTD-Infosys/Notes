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



