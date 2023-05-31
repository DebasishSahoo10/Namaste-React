# Namaste React Notes and Concpets

### Library Vs. Framework
- So the major difference between these two is actually regarding RULES. In a Framework rules are largely set ranging from setting a file name to most importan things like Flow of app like calling a specific type of function/state. And changing these rules will be another task.
- In library devs have much freedom reagrding these things. For an example we can name a componenet anything. we can call a function any where if it is available. but it is not like that libraries don't have any rules, yes they have but very basic rules and not as strict as Framework Rules.
- the one other difference will be, in a Library we can't use any Framework, but in a Framework we can use multiple libraries (and it works like we wrote our code in the Framework as per it rules and then the framework called our code and then our code will call the library we used)
### Why React is called React
The name "React" comes from the fact that the library is built around the concept of reacting to changes in a web application's state.
### Production Code vs. Development Code
Production code is all about size and performance, so it inlcudes a lot features arround that. But Development Version is all about Error Handling and Debugging, so it might ignore the performance steps but definately includes codes to find out potential errors and to debug things better.

---
### Why the need of arrow function came in ES6
- Arrow functions have a more concise syntax compared to traditional functions
- Arrow functions allow for an implicit return of the function. In traditional functions, you have to explicitly return a value
### Difference between normal and arrow function
 The value of the 'this' keyword inside an arrow function is based on the context in which the function is defined, whereas the value of 'this' inside a normal function depends on how the function is called. In other words, arrow functions have a lexical 'this' binding, while normal functions have a dynamic 'this' binding.
 ```javascript
const person = {
  name: 'John',
  age: 30,
  greet: function() {
    console.log('Hello, my name is ' + this.name);
  },
  greetArrow: () => {
    console.log('Hello, my name is ' + this.name);
  }
};

person.greet(); // output: Hello, my name is John
person.greetArrow(); // output: Hello, my name is undefined
```
```javascript
const obj = {
  name: 'John',
  greet: function() {
    const sayHello = () => {
      console.log('Hello, my name is ' + this.name);
    };
    sayHello();
  }
};

obj.greet(); // output: Hello, my name is John
```

---
### What should be on the GitIgnore
Anything that can be regenreated by your buildtool on the server should be put in the GITIGNORE. (thumb rule)
### Why React is Fast
It is not just React's features that makes it fast, it much more that goes into building the web app fueled on React, that makes the React app fast. e.g. Buildtools. React can't make a performant app alone, it needs a buildtool, and that buildtool need another helper codes too.
### What are Transitive Dependencies
A Tool in React can have its dependecies and those dependecies can have their own dependecies, this concepts is called Transitive Dependecies. And to track buildtools like vite create a Dependecy Tree.
### What is Tree Shaking
- Tree shaking is a technique used in modern JavaScript module bundlers, such as Webpack and Rollup(which is included in Vite), to eliminate unused code from a project's final build. The term "tree shaking" comes from the idea of shaking a tree to remove the dead leaves.
- The process of tree shaking begins by analyzing the project's module dependencies and building a dependency graph, or a map of all the imported modules and their dependencies. The module bundler then walks through this dependency graph and marks any code that is not referenced or used by the application. This process is often called "dead code elimination."
### What is the difference between `package.json` and `package-lock.json`
The main difference between package.json and package-lock.json is that the former is a configuration file that is manually created and maintained by developers, while the latter is an automatically generated file that provides a complete and accurate list of all the dependencies and their versions. package.json is used to specify the project's dependencies and configuration settings, while package-lock.json is used to ensure that those dependencies are installed consistently and reliably across different machines and environments.

---

### React Elements vs. React Component
React elements are plain JavaScript objects that describe what you want to see on the screen. They are lightweight and immutable, and represent a virtual view of a DOM element. An example of a React element would be:
```javascript
const element = <h1>Hello, world!</h1>;
```
React components, on the other hand, are reusable pieces of code that encapsulate the logic and rendering of a portion of the UI. They are typically created using JavaScript classes or functions, and can accept input data (known as "props") and state. An example of a React component would be:
```javascript
import React from 'react';

function Greeting(props) {
  return (
    <div>
      <h1>Hello, {props.name}!</h1>
      <p>Welcome to my website.</p>
    </div>
  );
}

export default Greeting;
```
### How Babel works in the background
It converts the JSX syntax into plain JavaScript code.
```javascript
// JSX code
const element = <h1>Hello, world!</h1>;

// Transpiled JavaScript code
const element = React.createElement("h1", null, "Hello, world!");
```
Babel also transforms other modern JavaScript syntax, allowing developers to write code using the latest language features without worrying about browser compatibility issues. We do not need to write polyfill. Babel does it automatically.
### NPM vs. NPX
- npx - executing commands without downloading packages
- npm - will download required packages
### Santisation in JSX
In React, sanitization is the process of cleaning and validating user input to prevent malicious code injection and other security vulnerabilities. Sanitizing user input is an important step in creating secure web applications.
### Component Composition
A component under another component is called Component Composition. Just a fancy name for Nested Component

---

### React.Fragment
React fragments are a simple yet elegant feature that enable grouping multiple sibling components without introducing any unnecessary markup in the rendered HTML. They serve as a cleaner alternative to using unnecessary divs in code, and you can create and render fragments in several ways. You should use React fragments when you want to add a parent element to fulfill the JSX syntax, but without introducing an extra node to the DOM.
### Virtual DOM : the secret superhero(Reconciliation and Fiber)
1. First Thing : When new elements are added to the UI, a virtual DOM, which is represented as a tree is created. Each element is a node on this tree. If the state of any of these elements changes, a new virtual DOM tree is created. This tree is then compared or “diffed” with the previous virtual DOM tree. Once this is done, the virtual DOM calculates the best possible method to make these changes to the real DOM. This ensures that there are minimal operations on the real DOM. Hence, reducing the performance cost of updating the real DOM. This Process is called Reconcilation. And the algorithim is called FIBER.
2. Second thing : in the process of DOM updation, the most expensive task is Reflow and Repaint. For that React follows a batch update mechanism to update the real DOM. Hence, leading to increased performance. This means that updates to the real DOM are sent in batches, instead of sending updates for every single change in state. The repainting of the UI is the most expensive part, and React efficiently ensures that the real DOM receives only batched updates to repaint the UI.
### What is the difference between a controlled component and an uncontrolled component?
1. A large part of React is this idea of having components control and manage their own state. What happens when we throw native HTML form elements (input, select, textarea, etc) into the mix? Should we have React be the "single source of truth" like we're used to doing with React or should we allow that form data to live in the DOM like we're used to typically doing with HTML form elements? These two questions are at the heart of controlled vs. uncontrolled components.
2. A controlled component is a component where React is in control and is the single source of truth for the form data. As you can see below, username doesn't live in the DOM but instead lives in our component state. Whenever we want to update username, we call setState as we're used to.
3. An uncontrolled component is where your form data is handled by the DOM, instead of inside your React component. It is done using useRef hooks.
### Describe how events are handled in React
1. In order to solve cross browser compatibility issues, your event handlers in React will be passed instances of SyntheticEvent, which is React's cross-browser wrapper around the browser's native event. These synthetic events have the same interface as native events you're used to, except they work identically across all browsers.
2. What's mildly interesting is that React doesn't actually attach events to the child nodes themselves. React will listen to all events at the top level using a single event listener. This is good for performance and it also means that React doesn't need to worry about keeping track of event listeners when updating the DOM. This concept is called Event Delegation.
### Event Delegation
Event delegation is a pattern used in React for handling events that involves adding a single event listener to a parent element instead of adding event listeners to individual child elements. When an event occurs on a child element, the event listener on the parent element is notified, and the parent element can handle the event. This is useful when you have many child elements and want to avoid adding event listeners to them. To make this concept happen React uses Event Bubbling.
### What is the second argument that can optionally be passed to setState and what is its purpose?
A callback function which will be invoked when setState has finished and the component is re-rendered. Something that's not spoken of a lot is that setState is asynchronous, which is why it takes in a second callback function to run it when the asynchronoys task has been done. Typically it's best to use another lifecycle method rather than relying on this callback function, but it's good to know it exists.
```javascript
this.setState(
  { username: 'tylermcginnis' },
  () => console.log('setState has finished and the component has re-rendered.')
)
```
### Why we need keys in React? When do we need keys in React?
When we render a set of same type of elements like a list of same kind of element or elements from a same source, then React can be confused when a state changes in that list, to render exactly which list item. so to make things easier, we give every list item a key so that it can find that exact unique piece which state has been changed.
### What is a Config Driven UI ?
A config-driven UI is a way of building user interfaces that uses configuration files to define the layout, styles, and other properties of UI elements. This approach makes it easier to customize the UI for different use cases or user groups, without the need for extensive coding.