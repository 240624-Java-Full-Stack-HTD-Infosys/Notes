# Real-World Application

- Since a Subject is an Observable, Consider a scenario where a selector is created for employee id.When you now subscribe to this selector / observable, everytime the employee id state changes, your observable emits the new employee id. using this you can bind html template variables to these observable which would update your employee id in your page automatically.