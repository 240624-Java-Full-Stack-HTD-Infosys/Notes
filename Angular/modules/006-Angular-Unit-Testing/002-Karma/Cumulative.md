# Cumulative for the  Karma
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The Basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To describe testing in Angular.
- To describe Karma.


</details>
<details><summary>Description</summary>

# Description

- Angular downloads and installs all the necessary files to the Angular project. When a new project is created, it is ready to be tested using Jasmine and Karma.

## Karma

Karma is a task runner for our tests. It uses a configuration file named `karma.conf.js` in order to set the startup file, the reporters, the testing framework, the browser among other things.

`karma.conf.js`:
```js
// Karma configuration file, see link for more information
// https://karma-runner.github.io/1.0/config/configuration-file.html

module.exports = function (config) {
  config.set({
    basePath: '',
    frameworks: ['jasmine', '@angular-devkit/build-angular'],
    plugins: [
      require('karma-jasmine'),
      require('karma-chrome-launcher'),
      require('karma-jasmine-html-reporter'),
      require('karma-coverage'),
      require('@angular-devkit/build-angular/plugins/karma')
    ],
    client: {
      jasmine: {
        // you can add configuration options for Jasmine here
        // the possible options are listed at https://jasmine.github.io/api/edge/Configuration.html
        // for example, you can disable the random execution with `random: false`
        // or set a specific seed with `seed: 4321`
      },
      clearContext: false // leave Jasmine Spec Runner output visible in browser
    },
    jasmineHtmlReporter: {
      suppressAll: true // removes the duplicated traces
    },
    coverageReporter: {
      dir: require('path').join(__dirname, './coverage/testing'),
      subdir: '.',
      reporters: [
        { type: 'html' },
        { type: 'text-summary' }
      ]
    },
    reporters: ['progress', 'kjhtml'],
    port: 9876,
    colors: true,
    logLevel: config.LOG_INFO,
    autoWatch: true,
    browsers: ['Chrome'],
    singleRun: false,
    restartOnFileChange: true
  });
};

```

</details>
<details><summary>Real World Application</summary>

# Real-World Application

- Any application uses automation testing to make sure that the application is working before its deployed.
- In Angular, karma and jasmine are used to perform unit tests, intergrated tests and end to end tests.
</details>
<details><summary>Implementation</summary> 

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



</details>
<details><summary>Summary</summary> 

# Summary

- Karma runs tests in Angular with the help of ``karma.conf.js` in order to set the startup file, the reporters, the testing framework, the browser among other things.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
