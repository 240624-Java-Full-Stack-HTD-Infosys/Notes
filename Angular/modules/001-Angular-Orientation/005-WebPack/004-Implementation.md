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








