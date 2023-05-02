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