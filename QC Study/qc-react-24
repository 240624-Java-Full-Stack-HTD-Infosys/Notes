
#### React Overview

* **What is React? Is it a library or framework? What's the difference between those?**
  * Keywords, concepts, or topics that should be in the response:
    * React is a UI library. It's a library not a framework because you call it in your code; it can be integrated into part of or the entire UI

* **Why use React?**
  * Keywords, concepts, or topics that should be in the response:
    * We use it to make `single page` front end applications
    * Lets us dynamically create and render components without having to refresh pages

* **What does it mean to be component-based? What does a component represent?**
  * Keywords, concepts, or topics that should be in the response:
    * Components are reusable parts of the UI that maintain a state and get rendered to the page
    * **Follow-up: Why use components?**
      * Increase reusability and maintainability
      * Also helps loosen code coupling within the application
      * Can pass data between components hierarchically as props

* **What is a single page application (SPA)?**
  * Keywords, concepts, or topics that should be in the response:
    * Single Page Application is a website design approach where each new page's content is served not from loading new HTML pages but generated dynamically with JS's ability to manipulate the DOM elements on the existing page itself
    * We can have many components that are rendered in one SINGLE page
    * It is constructed in a way that we only ever need to render one DOM object

* **What are some benefits and drawbacks of SPA?**
  * Keywords, concepts, or topics that should be in the response:
    * Benefit: allows users to continue consuming and interacting with the page while new elements are being updated or fetched, and can result in much faster interactions
    * Drawbacks / downsides
      * Accessibility
      * SEO rankings
      * If your content is purely static, it can worsen initial load times

* **Tell me how you would start up a new React project? What does `create react app` setup for you?**
  * Keywords, concepts, or topics that should be in the response:
    * You should use `npm` to install `react` and any other dependencies

#### Components

* **How would you create a component?**
  * Keywords, concepts, or topics that should be in the response:
    * Create either a JS class or function
  * **Follow-up: what does a component have to return?**
    * Class components need a `render` method that returns JSX
    * Functional components directly return JSX
  * **Follow-up: What is the difference between a functional and a class component?**
    * Functional - before hooks, could not modify state and only used as 'display' component
    * Class - utilizes lifecycle methods and `render` method

* **What is the `App.tsx`? Why do we structure it in that way?**
  * Keywords, concepts, or topics that should be in the response:
    * Main component, entry point for our application, usually do routing within it
    * This is where we render the root node for the DOM object
    * It's structured like this because easy to maintain and at the end of the day we only want one root for everything else

* **What are "props"? What is state? What data should be put in which?**
  * Keywords, concepts, or topics that should be in the response:
    * Props are read-only; they are passed into the component
    * State is the immutable object representing the current state of the component
  * **Follow-up: how do you edit state in functional and class components?**
    * Class components: use `setState()` and replace the prev state object instead of editing it directly
    * Functional components: get update function from `useState()` hook
    * Remember: state is immutable, so cannot edit directly; this follows functional programming and prevent consistency problems

* **What is the lifecycle of a component?**
  * Class components use specific lifecycle methods:
    * Constructor - use for initializing state
    * `render()` - returns the JSX to be compiled and rendered onto the browser
    * `componentDidMount()` - runs once, after the component is rendered
    * `componentDidUpdate()` - runs after every update of the component
    * `componentWillUnmount()` - runs before the component is removed from the DOM

* **What are React hooks? How do we use them?**
  * Keywords, concepts, or topics that should be in the response:
    * React hooks are functions we can call in order to access certain functionalities
    * They all start with `use` such as `useStyle()`, `useState()`, `useEffect()`, `useReducer()`
    * We call them hooks because they allow us to `hook` into certain aspects of a component whether it be style or lifecycle
  * **Follow-up: What do these hooks let us do?**
    * `useState()`
      * returns an array of the following
        * Index 0, we have the state object
        * Index 1, we have the function to use to update that object state
    * `useEffect()`
      * Allows us to manage side-effects that aren't related to rendering the component
      * Typically actions such as logging or fetching data will utilize `useEffect()`
      * Takes in 2 params
        * A callback function denoting what action you want to perform
        * A dependency array of state values that act as triggers for the action on change
    * `useReducer()`
      * Allows us a better way of updating complex state logic
      * Takes in 2 params
        * The callback function with logic to update the state
        * The initial state of the object

* **How do we save data in a component?**
  * Keywords, concepts, or topics that should be in the response:
    * To save data we can use React component states
    * If we are using class components, we can set this initial state directly in the constructor
    * If we are using a function component, we can use the `useState()` hook to create and offer a method to change state

#### Routing

* **What is routing and how would you do routing in React?**
  * Keywords, concepts, or topics that should be in the response:
    * Need to install `react-router` using `npm`
    * Use the `BrowserRouter` component to provide context where routing will work
    * Use `Link` component to link to a particular route
    * Use `Routes` and `Route` components to link routes to particular components that get rendered

### IMPORTANCE: HIGH

[Back to top](#unit-react)

#### File / Project Structure

* **What is the `package.json` file?**
  * Keywords, concepts, or topics that should be in the response:
    * Lists our dependencies
    * Lists our scripts
      * Start, test are aliases for `npm run [script]`
    * Run the build script to show the target folder

* **What is the build folder?**
  * Keywords, concepts, or topics that should be in the response:
    * After running the command `npm run build` a folder called build is created with our self-container app

#### JSX and Data Binding

* **What is JSX? What does it compile into? How to include JS code in JSX?**
  * Keywords, concepts, or topics that should be in the response:
    * JSX is an extension syntax to JS - it lets you write HTML and JS code together; compiles into JS
    * Not required but helps with development
    * Write JS code by using curly braces `{like this}`

* **What are some of the differences between JSX HTML and normal HTML?**
  * Keywords, concepts, or topics that should be in the response:
    * Attribute names
      * Example class => className
      * You can also create your own "attributes" which are called props
    * Tag names
      * HTML tag: `<p>`
      * Component tag: `<SomeComponent>`
      * We can directly add JS into JSX HTML by using { } where as in HTML you cannot do this

* **Does React have 1-way or 2-way data binding and data flow?**
  * Keywords, concepts, or topics that should be in the response:
    * 1-way data binding
    * Data always flows "down" to components nested within them

* **If a parent component has data that a child component needs to access, what should you do?**
  * Keywords, concepts, or topics that should be in the response:
    * Pass in the data through `props` to the child

* **If you have state in two child components that a parent component needs access to, what is a good solution for that?**
  * Keywords, concepts, or topics that should be in the response:
    * Lift the state up to the parent component and then pass it into each child via `props`

#### TypeScript

* **How do we do type checking in React?**
  * Keywords, concepts, or topics that should be in the response:
    * Without TypeScript, we can assign `propTypes` special property
    * Otherwise, use TypeScript: `npm install typescript`

* **What are some pros/cons of using TypeScript in a React application?**
  * Keywords, concepts, or topics that should be in the response:
    * Pros: strict type checking; intellisense; features like interfaces, decorators, and access modifiers
    * Cons: adds overhead and extra transpilation; may be unnecessary for small projects

#### Forms and AJAX

* **How would you handle forms and submitting forms with React?**
  * Keywords, concepts, or topics that should be in the response:
    * Use "controlled components" where the state of the form is based on the state of the React component
    * Not recommended, but you can use uncontrolled component with a Ref to get form values from the DOM

* **How do you recommend making an AJAX call in React? Which library have you used? Why not use `fetch` directly?**
  * Keywords, concepts, or topics that should be in the response:
    * Can use AJAX itself or `fetch`, but a library like Axios is a good idea b/c can centrally configure all requests
    * Example: need to include JWT token with every request for authorization

### IMPORTANCE: REGULAR

[Back to top](#unit-react)

#### React and the DOM

* **What is the difference between React and ReactDOM?**
  * Keywords, concepts, or topics that should be in the response:
    * React is a higher level package for both ReactDOM and React Native
    * ReactDOM is strictly the web implementation of React

* **What is ReactDOM.render?**
  * Keywords, concepts, or topics that should be in the response:
    * ReactDOM takes 2 arguments
      * The element to render
      * The location to add the element to in the DOM

* **What is the virtual DOM?**
  * Keywords, concepts, or topics that should be in the response:
    * An "ideal" or "virtual" state of the UI that is managed by React and kept in sync with the actual DOM
    * Improves performance by only requiring changing the actual DOM when needed
  * **Follow-up: How does virtual DOM compare to the DOM?**
    * Kept in sync with the real DOM by a library such as ReactDOM. The process is called reconciliation
    * You tell react what state you want the UI to be in, and it makes sure the DOM matches that state. This abstracts out attribute manipulation, event handling and manual DOM updates that you would otherwise have to do

#### Types of Components

* **What is the purpose of a container component?**
  * Keywords, concepts, or topics that should be in the response:
    * A container component holds the state that it then passes to "display" child components

* **What is a pure component vs a normal one vs a higher order one?**
  * Keywords, concepts, or topics that should be in the response:
    * `Pure Component`
      * State/Props should be immutable
      * State/Props should not have hierarchy
      * You should call forceUpdate() when data changes
      * We do this when we need performance boosts
      * Dumb/Stateless components
    * `Normal Component`
      * This can be a smart or stateful component which may update or change state
      * It will usually contain some logic that will make things happen
    * `Higher Order Component`
      * This is a component that takes a component and returns a slightly modified version of this component

#### Miscellaneous

* **What should you remember to include as a prop for lists of elements?**
  * Keywords, concepts, or topics that should be in the response:
    * Pass in a `key` prop that uniquely identifies the list item
    * Helps React know which items have changed, been added, or removed

* **What are the roles of Babel and Webpack?**
  * Keywords, concepts, or topics that should be in the response:
    * Babel
      * Free open source JS transpiler or transcompiler that will turn things like JSX and tsx into valid JS code
      * Make sure to start all components with capital letter, this is how Babel knows its a component it has to transpile
    * Webpack
      * This is a packaging tool that takes all the different files and modules and build them into a web package to use within the browser

* **What are some options for styling your React components?**
  * Keywords, concepts, or topics that should be in the response:
    * Preferred: use the `className` prop
    * Optional: use inline styling, or "CSS-in-JS" where the styling is defined in JS

* **How do you test React components and code that you write?**
  * Keywords, concepts, or topics that should be in the response:
    * Jest is a unit testing tool you can use to test your code
    * Enzyme is a testing utility to make it easier to test your components' output

## Flux - Redux

### IMPORTANCE: Critical

[Back to top](#unit-react)

* **What is the Flux design pattern?**
  * Keywords, concepts, or topics that should be in the response:
    * A pattern for state management with unidirectional data flow: from action -> dispatcher -> store -> view

* **What is Redux? How is Redux related to Flux?**
  * Keywords, concepts, or topics that should be in the response:
    * A global state management library
    * Useful for complex apps where managing state becomes too unwieldy
    * Redux is the popular implementation of Flux

* **What are the core principles of Redux?**
  * Keywords, concepts, or topics that should be in the response:
    * Single source of truth
      * The global state of your app is put away in an object tree inside a single store
    * State is read-only
      * The state can only be changed by emitting an action, an object that explains what has happened
    * Changes are made with pure functions
      * This is to define how the state tree is being transformed by the actions, you have to write pure reducers

* **What is an Action in Redux?**
  * Keywords, concepts, or topics that should be in the response:
    * Plain JS objects which contain a type field.
    * Considered as an event that can describe something that has happened in the application
    * Should always contain a small amount of information that is needed to mention what has happened
  * Possible follow-up questions:
    * **What is the following code snippet doing?**

      ```tsx
      const addAction = {
          type: 'ADD',
          payload: 'Buy-car'
      }
      ```

    * Ans: we are adding an action to our Redux containing the type `ADD` and the payload `Buy-car`
  
* **What is 'store' in Redux?**
  * Keywords, concepts, or topics that should be in the response:
    * Carries all the states, reducers and actions that create the app
      * It holds the state of the current Application from inside
      * store.getState(); allows access to the current state
      * store.dispatch(action); allows the state to be updated
      * store.subscriber(listener); allows to register listener callbacks

* **What are some store methods?**
  * Keywords, concepts, or topics that should be in the response:
    * getState()
    * dispatch(action)
    * subscribe(listener)
    * replaceReducer(nextReducer)

* **How to access Redux store outside a react component?**
  * Keywords, concepts, or topics that should be in the response:
    * You need to export the store from the module where it has been created with createStore
  * Possible follow-up questions:
    * **What is the following code doing?**

      ```tsx
      store = createStore(myReducer);
      export default store;
      ```

    * Ans: We are exporting the store from the module where it has been created using `createStore`

* **What are reducers in redux?**
  * Keywords, concepts, or topics that should be in the response:
    * Pure functions that take the previous state and an action, then it returns the next state
    * `(previousState, action) => newState`
    * Is a type of function that would pass to `Array.prototype.reduce(reducer, ?initialValue)`
    * Essential that the reducer stays pure

### IMPORTANCE: High

[Back to top](#unit-react)

* **What is the difference between mapStateToProps() and mapDispatchToProps()?**
  * Keywords, concepts, or topics that should be in the response:
    * | `mapStateToProps()` | `mapDispatchToProps()` |
      | ----------------  | -------------------- |
      | Is a function that is used to provide the stored data to the component | Is a function that is used to provide the action creators with props to the component |
      | All the results of mapStateToProps() should be the plain object that will later be merged into the component's prop | All the action creators are wrapped in the dispatcher call so that they may be called upon directly and will be merged into the component's prop |
      | Used to connect the redux state to the props of the react component | Used to connect redux actions to the react props |

* **Do you need to keep all component states in the Redux store?**
  * Keywords, concepts, or topics that should be in the response:
    * No because we have to keep our application state as small as possible
    * Should only do so if it makes our lives easier while using Dev Tools

### IMPORTANCE: Regular

[Back to top](#unit-react)

* **What is Redux DevTools?**
  * Keywords, concepts, or topics that should be in the response:
    * Time travel environment that allows live editing for Redux with action replay, hot reloading, and customizable UI
    * Can use in any browser, Chrome or Firefox

* **What are some features of the Redux DevTools?**
  * Keywords, concepts, or topics that should be in the response:
    * Allows us to inspect all the states and action payload
    * Allows us to go back into the time simply by cancelling the actions
    * Each stage action will be re-evaluated in case you change the reducer code
    * With the help of `persistState()` store enhancer, you can continue your debug sessions across page reloads

* **How to structure Redux top-level directories?**
  * Keywords, concepts, or topics that should be in the response:
    * `Components`
      * Used for 'dumb' React components that are unfamiliar with Redux
    * `Containers`
      * Used for 'smart' React components which are connected to the Redux
    * `Actions`
      * Used for all the action creators, where the file name should be corresponding to the part of the app
    * `Reducers`
      * Used for all the reducers where the file name is corresponding to the state key
    * `Store`
      * Used for store initialization. This directory works best in small and mid-level size apps

* **What is the purpose of constants in Redux?**
  * Keywords, concepts, or topics that should be in the response:
    * Allows us to find all the usages of specific functionality across the project
    * Also prevents us from making mistakes such as typos. These will gives us a Reference Error immediately

* **What is a "thunk"? What is `redux-thunk` used for?**
  * Keywords, concepts, or topics that should be in the response:
    * Thunk is a function that wraps an expression to delay its evaluation  
    * Used for delaying dispatch of an action or based on a condition

## React Query

* **What is a Query Key in React Query?**
  * Keywords, concepts, or topics that should be in the response:
    * The name of a cache

* **What is the difference between a mutation and a query in React Query?**
  * Keywords, concepts, or topics that should be in the response:
    * Mutations alter data
    * Queries read data

## Saga

* **What is an effect in Saga?**
  * Keywords, concepts, or topics that should be in the response:
    * A JS object that instructs the Saga middleware on what to do

* **What are helper functions in Saga?**
  * Keywords, concepts, or topics that should be in the response:
    * Wrappers like `takeEvery()` that modify how a watcher saga operates

* **Explain what a `worker Saga`, `watcher Saga`, and a `Root Saga` is.**
  * Keywords, concepts, or topics that should be in the response:
    * `worker Saga`:
      * A Saga that takes in an action, processes it, and usually dispatches a different action to the reducer
    * `watcher Saga`:
      * A Saga that intercepts specific actions
    * `root Saga`:
      * A Saga that lists all Sagas used

* **When would we integrate Saga into Redux?**
  * Keywords, concepts, or topics that should be in the response:
    * The application we are creating has a lot of asynchronous operations




### React Practicals

* **What is the code snippet doing? Explain**

    ```jsx
    function HelloWorld(){
      return(
        <div>
          <h1>Hello World!</h1>
        </div>
      );
    }
    ```

  * Creates a "HelloWorld" component with the text "Hello World!" inside a "div"
  * Now when we want to render the component, we can simply say `<Hello World/>` in our App component
  * We can list the component as many times as we would like to as long as it's wrapped in another tag
  * Components are valuable for their reusability and their ability to manage their own independent state

* **Given the component above, what happens when the App component has this code?**

    ```jsx
    function App() {
      const arr = [1,2,3,4,5]
      return (
        arr.map((x, idx) => {
          <HelloWorld />
        })
      )
    }
    ```
  
  * **Follow-up: If I want to print the number (1,2,3,4,5) associated with each "HelloWorld" component, how can you modify the code?**
    * Edit `HelloWorld` to take in props, and pass in `x` param to it in the `App` component
    * Change the text in the `<h1>` to `Hello World {variable}!`

* **Explain what the component below is doing. What should be added to complete the functionality?**
  * Keywords, concepts, or topics that should be in the response:
    * Data binding
    * Event handling
    * "useState" hook
    * add "onChange" event handler to JSX input tags

  ```javascript
  function LoginForm() {
    const [username, changeUsername] = useState("")
    const [password, changePassword] = useState("")

    const handleUsernameChange = (e: React.ChangeEvent<HTMLInputElement>) => {
      changeUsername(e.target.value)
    }
    const handlePasswordChange = (e: React.ChangeEvent<HTMLInputElement>) => {
      changePassword(e.target.value)
    }
    return (
      <form>
        <input id="username" type="text">
        <input id="pw" type="password">
      </form>
    )
  }
  ```

* **Write some code to show how you handle events in React**
  * Keywords, concepts, or topics that should be in the response:
    * Use event binding: `<button onClick={myClickHandler}></button>`
    * For sending parameters: `<button onClick={(e) => this.deleteRow(id, e)}>Delete Row</button>`
    * Define `myClickHandler` function in your component somewhere

* **Explain what the code below does**

  ```jsx
  render() {
      const myBooleanValue = Math.random() < 0.5;
      return <div>{myBooleanValue && <SomeComponent />}</div>
  }
  ```

  * Conditional rendering - if `myBooleanValue` is `true`, display `SomeComponent`; otherwise do not render
  * In the code, `myBooleanValue` will be randomized
  * **Follow-up: can you edit the code and add a button that will flip the boolean value?**
    * Need to store the boolean in state; use the `useState` hook and initial value can be kept random
    * Add `<button onClick={() => setMyBooleanValue(!myBooleanValue)}>`
