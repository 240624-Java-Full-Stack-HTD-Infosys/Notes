# Real World Application

- Angular works using a component-based architecture. 
- Initially `constructor()` is called, followed by `ngOnChnages()`, `ngOnInit()`, with every keystroke, `ngDoCheck()` is called, followed by `noAfterContentInit()`, `ngAfterContentChecked()`, `ngAfterViewInit()`, `ngAfterViewChecked()` and finally `ngOnDestroy()`, if the component is destroyed.