# Implementation

- The following command is run to test an Angular project.

```properties
ng test
```

- The `ng test` command builds the application in the watch mode.
- It also launches the Karma test runner.

The console output:

``` console
√ Browser application bundle generation complete.
06 12 2022 17:01:52.617:WARN [karma]: No captured browser, open http://localhost:9876/
06 12 2022 17:01:52.652:INFO [karma-server]: Karma v6.4.1 server started at http://localhost:9876/
06 12 2022 17:01:52.653:INFO [launcher]: Launching browsers Chrome with concurrency unlimited
06 12 2022 17:01:52.674:INFO [launcher]: Starting browser Chrome
06 12 2022 17:01:54.094:INFO [Chrome 107.0.0.0 (Windows 10)]: Connected on socket gI90mbnSGq_mXxo1AAAB with id 62600632
Chrome 107.0.0.0 (Windows 10): Executed 3 of 3 SUCCESS (0.198 secs / 0.173 secs)
TOTAL: 3 SUCCESS
```


![Karma](/modules_new/resources/karma.png)

- The browser reloads dynamically everytime a change is made in the Angular project with the help of Karma.



