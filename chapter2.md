# Chapter 2 - Functions & Scope

- [Introduction to Functions - Defining Functions, Calling Functions, and Function Parameters](#introduction-to-functions---defining-functions-calling-functions-and-function-parameters)
- [Function expressions vs. function declarations](#function-expressions-vs-function-declarations)
- [Scope and variable hoisting](#scope-and-variable-hoisting)
- [Closures and their applications](#closures-and-their-applications)
- [Arrow functions and their advantages](#arrow-functions-and-their-advantages)
- [Callback Functions](#callback-functions)
        
---

## Introduction to Functions - Defining Functions, Calling Functions, and Function Parameters

Create a new file named `functions.js` in VS Code. You can copy the example code from each step and execute from the terminal using `node functions.js`.

### Defining Functions

Functions in JS are blocks of code that can be defined and reused to perform a specific task.

#### Syntax
```js
function functionName(parameters) {
    // code block to execute
}
```

#### Example
```js
function greet() {
    console.log("Hello, world!");
}
```

### Calling Functions

Once a function is defined, it can be called or invoked to execute the code inside it.

#### Syntax
```js
functionName(); // calling a function without parameters
```
#### Example
```js
greet(); // Output: Hello, world!
```
### Function Parameters

Functions can accept input data called parameters, which are specified when defining the function.

Parameters are placeholders for values that will be provided when the function is called.

#### Syntax
```js
function functionName(parameter1, parameter2, ...) {
    // code block to execute
}
```

#### Example
```js
function greet(name) {
    console.log("Hello, " + name + "!");
}
```

### Calling Functions with Parameters

When calling a function with parameters, values are passed to the function as arguments.

#### Syntax
```js
functionName(argument1, argument2, ...); // calling a function with parameters
```

#### Example
```js
greet("John"); // Output: Hello, John!
```

### Returning Values from Functions

Functions can also return values using the return statement, which ends the function execution and returns a value to the caller.

#### Syntax
```js
function functionName(parameters) {
    // code block to execute
    return value;
}
```

#### Example
```js
function add(a, b) {
    return a + b;
}
let result = add(5, 3);
console.log(result); // Output: 8
```

---

## Function expressions vs. function declarations

### Function Declarations
Function declarations are one of the two ways to define a function in JavaScript. They are defined using the function keyword followed by the function name and a block of code enclosed in curly braces.

```js
// Function Declaration
function greet() {
    console.log("Hello, world!");
}
```

#### Key Points

- Function declarations are *hoisted* (we cover hoisting in the next section), which means they are loaded into memory during the compile phase before the code execution.
- They can be called before they are defined in the code.


### Function Expressions
Function expressions are another way to define a function in JavaScript. They involve assigning a function to a variable. In function expressions, the function does not have a name (anonymous function) unless explicitly given one.

```js
// Function Expression
let greet = function() {
    console.log("Hello, world!");
};
```

#### Key Points

- Function expressions are *not hoisted*. They are treated like any other variable assignment and are not accessible before the line they are defined on.
- They provide more flexibility, as they can be assigned to variables and passed as arguments to other functions.

### Code Examples

#### Function Declaration
```js
// Function Declaration
function greet() {
    console.log("Hello, world!");
}

// Call the function
greet(); // Output: Hello, world!
```

#### Function Expression
```js
// Function Expression
let greet = function() {
    console.log("Hello, world!");
};

// Call the function
greet(); // Output: Hello, world!
```

### Choosing Between Function Declarations and Function Expressions

Use function declarations when you need to define a function that should be accessible throughout your code, even before it's declared.

Use function expressions when you need to assign a function to a variable, or when you want to create a function conditionally or dynamically.

## Scope and variable hoisting

### Scope
Scope refers to the visibility and accessibility of variables within different parts of a JavaScript program. JavaScript has two main types of scope: *global scope* and *local scope*.

#### Global Scope

Variables declared *outside* of any function have global scope and can be accessed from anywhere within the program.

#### Local Scope

Variables declared **inside** a function have local scope and can only be accessed within that function.

### Variable Hoisting
Variable hoisting is a JavaScript behavior where variable declarations are moved to the *top of their containing scope* during the compile phase. This means that regardless of where a variable is declared in a function or block, it behaves as if it were declared at the top of its containing scope.

#### Examples

##### Global Scope
```js
// Variable in global scope
let globalVar = 'I am global';

function func() {
    console.log(globalVar); // Output: I am global
}

func(); // Call the function
```

##### Local Scope
```js
function func() {
    // Variable in local scope
    let localVar = 'I am local';
    console.log(localVar); // Output: I am local
}

func(); // Call the function
// console.log(localVar); // Error: localVar is not defined (outside the function scope)
```

##### Variable Hoisting
```js
console.log(x); // Output: undefined (variable is hoisted, but not yet initialized)
var x = 5;
console.log(x); // Output: 5
```

In the example above, even though the variable `x` is declared after the first `console.log()` statement, it doesn't cause an error because variable declarations are *hoisted* to the top of their containing scope. However, the assignment `(x = 5)` remains in its original position.

> NOTE: Variable hoisting only applies to variable declarations (using `var`), not variable initializations or assignments. For `let` and `const`, they are hoisted to the top of their block scope, but they are not initialized, and accessing them before the declaration results in a ReferenceError.

---

## Closures and their applications

Closures are an important concept in JavaScript that allows functions to retain access to variables from their parent scope even after the parent function has finished executing. 

### Understanding Closures

A closure is formed when a function is defined within another function (outer function), and the inner function retains access to the variables and parameters of the outer function, even *after* the outer function has finished executing.

### Applications of Closures

1. Encapsulation

Closures can be used to create private variables and functions, encapsulating them within a scope that prevents external access.

```js
function createCounter() {
    let count = 0; // count is a private variable encapsulated within the closure
    
    return function() {
        return ++count;
    };
}

let counter = createCounter();
console.log(counter()); // Output: 1
console.log(counter()); // Output: 2
```

2. Data Hiding

Closures can hide implementation details and expose only necessary functionality, enhancing data privacy and security.

```js
function createUser(name, age) {
    return {
        getName: function() {
            return name;
        },
        getAge: function() {
            return age;
        }
    };
}

let user = createUser('John', 30);
console.log(user.getName()); // Output: John
console.log(user.getAge()); // Output: 30
```

3. Function Factories

Closures can be used to create function factories that generate specialized functions with preset configurations.

```js
function createMultiplier(factor) {
    return function(num) {
        return num * factor;
    };
}

let double = createMultiplier(2);
console.log(double(5)); // Output: 10

let triple = createMultiplier(3);
console.log(triple(5)); // Output: 15
```

4. Event Handlers

Closures are commonly used in *event handlers* to maintain access to the surrounding context, even when the event occurs asynchronously.

```js
function showMessage(message) {
    let btn = document.getElementById('btn');
    btn.addEventListener('click', function() {
        alert(message); // Accesses the message variable from the outer function
    });
}

showMessage('Hello, world!');
```
---

## Arrow functions and their advantages

Arrow functions are a concise way to write functions in JavaScript, introduced in ECMAScript 6 (ES6). They provide a more compact syntax compared to traditional function expressions, especially for short, single-line functions. 

Arrow functions are defined using a simplified syntax with an arrow (=>) symbol, hence the name "arrow functions". They offer several advantages over traditional function expressions.

1. Concise Syntax
Arrow functions have a shorter and more succinct syntax compared to traditional function expressions, making the code cleaner and easier to read.

2. Implicit Return
Arrow functions automatically return the result of the expression without needing an explicit `return` statement if the function body consists of a single expression.

3. Lexical this Binding
Arrow functions lexically bind the value of `this`, meaning they inherit the `this` value from the enclosing scope where the arrow function is defined, rather than having their own `this` value.

### Examples

#### Concise Syntax
```js
// Traditional function expression
let add = function(a, b) {
    return a + b;
};

// Arrow function
let add = (a, b) => a + b;
```

#### Implicit Return
```js
// Traditional function expression
let double = function(num) {
    return num * 2;
};

// Arrow function with implicit return
let double = num => num * 2;
```

#### Lexical `this` Binding
```js
// Traditional function expression
function Person() {
    this.age = 0;

    setInterval(function() {
        this.age++; // 'this' refers to the global object (window) in this context
        console.log(this.age);
    }, 1000);
}

let person = new Person(); // Outputs NaN repeatedly

// Arrow function with lexical 'this' binding
function Person() {
    this.age = 0;

    setInterval(() => {
        this.age++; // 'this' refers to the instance of Person
        console.log(this.age);
    }, 1000);
}

let person = new Person(); // Outputs incrementing numbers as expected
```

### Advantages of Arrow Functions

1. Arrow functions provide a more concise and expressive syntax, reducing boilerplate code.
2. They offer implicit return for single-line expressions, enhancing code readability.
3. Arrow functions lexically bind the value of `this`, preventing issues with dynamic scoping.
4. They are particularly useful for writing callback functions and handling asynchronous code.

---

## Callback Functions

A *callback function* is a function that is passed as an *argument* to another function, and it is *invoked or called within that other function*. The primary purpose of a callback function is to be executed at a later time, often after some asynchronous operation completes or in response to an event.

### How Callback Functions Work

When a function accepts another function (callback) as an argument, it can call the callback function one or more times inside its body.

The callback function is defined separately and passed as an argument to the *higher-order function*.

> Higher-order functions are functions that can accept other functions as arguments and/or return functions as output. In JavaScript, functions are first-class citizens, meaning they can be treated as values and passed around like any other data type. 

The higher-order function can then invoke the callback function one or more times, either synchronously or asynchronously, depending on the context.

### Example

```js
// Higher-order function that accepts a callback
function doSomething(callback) {
    console.log("Start of doSomething");
    // Perform some task
    callback(); // Invoke the callback function
    console.log("End of doSomething");
}

// Callback function definition
function callbackFunction() {
    console.log("Inside callbackFunction");
}

// Passing the callback function to the higher-order function
doSomething(callbackFunction);
```

#### Output

```
Start of doSomething
Inside callbackFunction
End of doSomething
```

### When Are Callbacks Used?

1. Callback functions are commonly used with asynchronous operations such as AJAX requests, setTimeout, setInterval, event listeners, and file I/O operations.
2. Callback functions are used to handle events in web development, such as button clicks, mouse movements, keyboard inputs, etc.
3. Callback functions can be passed to array methods like `forEach`, `map`, `filter`, and `reduce` to perform operations on array elements, which we will see in the next chapter.

---
[Chapter 3 - Working with Arrays >>](chapter3.md)