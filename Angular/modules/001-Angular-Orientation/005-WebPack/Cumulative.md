# Cumulative for the  WebPack
<details><summary>Prerequisites and Learning Objectives</summary>

# Prerequisites

- Sound knowledge of HTML, CSS, and JavaScript.
- The basic idea of the MVC (Model-View-Controller) architecture.
- Basic knowledge about TypeScript.


# Learning Objectives

- To define Webpack.
</details>
<details><summary>Description</summary>

# Description

## Webpack

- Webpack is a powerful module bundler.
-  A JavaScript file that  contains all the files that belong together and served to client in a response to single file request is called bundle.
-  A bundle can include JS, CSS, HTML and almost any other type of files.

The following files can be configured in webpack:

- **Entry**: The module where webpack starts.
- **Output**: The bundles created by webpack are emmited here.
- **Loaders**: Used in webpack to process more than JavaScript files.
- **Plugins**: A JavaScript object that has an apply method. This apply method is called by the webpack compiler, giving access to the entire compilation lifecycle.
  
</details>
<details><summary>Real World Application</summary>

# Real-World Application

- Angular, React and Vue use webpack module bundler.
</details>
<details><summary>Implementation</summary> 

# Implementation

## Webpack in Angular CLI


Create an angular project using 

```properties
ng new webpack-demo-project
```

Run the application using

```
cd webpack
ng serve
```

open browser at [ http:\\\localhost:4200](http://localhost:4200/)


In order to configure webpack the following files are needed.

- `package.json`
- `src/tsconfig.json`
- `webpack.config.js`
- `karma.conf.js`
- `config/helpers.js`

But there is no `webpack.config.js` in a normal Angular project.

- But if you naviate to  the directory `node_modules\@angular\cli` and to the `package.json` file the following dependencies are found.


```json
  "dependencies": {

    "webpack": "~3.11.0",
    "webpack-dev-middleware": "~1.12.0",
    "webpack-dev-server": "~2.11.0",
    "webpack-merge": "^4.1.0",
    "webpack-sources": "^1.0.0",
    "webpack-subresource-integrity": "^1.0.1"
  }
```

- In node_modules all these finds can be found, which proves that webpack is installed.

## Accessing webpack Config 

- The following code is implemented once the application is built.

```properties
ng eject
```

This code  will do the following:

- Generates a `webpack.config.js` file in the root of our project based on the current build.
- Sets the ejected flag to true in `.angular-cli.json`.
- Updates the scripts in `package.json` to run based on webpack rather than Angular CLI.


In order to run the project the following code is implemented.

1. Installation

```properties
npm install
```

2. To run application

```properties
npm run start
```
The application runs on `webpack-dev-server --port=4200`.

open browser at [ http:\\\localhost:4200](http://localhost:4200/)

to see application running in development server.

<i><b>Note</b>:If `ng serve` or `ng build` or anything related to ng project the following error occurs.

```properties
An ejected project cannot use the build command anymore.
```

</i>








</details>
<details><summary>Summary</summary> 

# Summary

- Webpack is a module bundler that bundles all the files like JS, CSS, HTML and almost any other type of files that belong together. 
- Web pack serves the bundle to client in a response to single file request is called bundle.
</details>
<details><summary>Practice Questions</summary>

[Practice Questions](./Quiz.gift)</details>
