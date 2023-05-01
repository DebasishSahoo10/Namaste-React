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
### Difference between 
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