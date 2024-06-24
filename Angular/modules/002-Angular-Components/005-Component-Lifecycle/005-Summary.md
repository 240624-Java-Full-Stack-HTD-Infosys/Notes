# Summary

Angular Lifecycle hooks describe the life cycle of a Component.

- Component lifecycle starts with `constructor()` followed by eight lifecycle hooks.

1. **`ngOnChanges`**: When an input/output binding value changes.
2. **`ngOnInit`**: After the first `ngOnChanges`.
3. **`ngDoCheck`**: Developer's custom change detection.
4. **`ngAfterContentInit`**: After component content initialized.
5. **`ngAfterContentChecked`**: After every check of component content.
6. **`ngAfterViewInit`**: After a component's views are initialized.
7. **`ngAfterViewChecked`**: After every check of a component's views.
8. **`ngOnDestroy`**: Just before the component/directive is destroyed.