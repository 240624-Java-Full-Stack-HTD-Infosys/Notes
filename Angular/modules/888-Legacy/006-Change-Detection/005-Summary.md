# Summary

- View and Model in an Angular application are in sync due to the change detection process.
- Every component has its change detector and when a change occurs the change detection is done from the root component to the respective component.
- This process makes the application slow.
- This problem can be resolved by setting Angular change detection to onPush.