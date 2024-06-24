# Summary

- View Encapsulation is an important feature of Angular, to encapsulate components CSS into components view.

Types of view encapsulation:

1. `ViewEncapuslation.Emulated`: default view, limits CSS styles scope to component level.
2. `ViewEncapuslation.None`: sets CSS styles scope to global.
3. `ViewEncapuslation.ShadowDom`: encloses CSS styles under shadow DOM. Global css styles are not applicable.