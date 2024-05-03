# JavaScript

This guide builds on the [JS fundamentals introduction](https://github.com/bjssacademy/fundamentals-js), and therefore assumes you have a basic understanding and have Node and VS Code installed already, in which case you can start at [Chapter 2](chapter2.md).

If not however, you'll find the rest of this section covers getting set up and the basic JavaScript syntax.

---

## Chapters

1. [Setting Up & Basics](readme.md#basics-of-javascript-syntax-variables-data-types-operators-and-trycatch)
2. [Functions & Scope](chapter2.md)
3. [Working with Arrays](chapter3.md)
4. [Working with Objects](chapter4.md)
5. [Asynchronous JavaScript](chapter5.md)
6. [Destructuring & Spread/Rest](chapter6.md)

---

## Setting Up

We are assuming that you have Node installed, but if not follow the instructions below.

### Node.js
https://nodejs.org/en/download

Node is a Javascript runtime; we need it to run JS locally when not in a browser.

To run .js files outside of a browser, navigate to the folder in the terminal and type:

`node filename.js `

to execute the file (replace `filename.js` with the actual name of your file)

### VS Code

We will use VS Code as our IDE. You can download and install VS Code from [here](https://code.visualstudio.com/).

---

<!-- TOC -->

- [JavaScript](#javascript)
    - [Chapters](#chapters)
    - [Setting Up](#setting-up)
        - [Node.js](#nodejs)
        - [VS Code](#vs-code)
    - [Basics of JavaScript Syntax: Variables, Data Types, Operators, and Try/Catch](#basics-of-javascript-syntax-variables-data-types-operators-and-trycatch)
        - [Variables](#variables)
            - [Guidelines](#guidelines)
        - [Data Types](#data-types)
        - [Operators](#operators)
    - [Control Flow - if Statements, switch Statements, and Ternary Operators](#control-flow---if-statements-switch-statements-and-ternary-operators)
        - [If Statements](#if-statements)
                - [Example](#example)
        - [Switch Statements](#switch-statements)
            - [Example](#example)
        - [Ternary Operator:](#ternary-operator)
            - [Syntax](#syntax)
            - [Example](#example)
    - [Loops - for Loop, while Loop, do-while Loop, and Loop Control Statements](#loops---for-loop-while-loop-do-while-loop-and-loop-control-statements)
        - [For Loop](#for-loop)
            - [Syntax](#syntax)
            - [Example](#example)
        - [While Loop](#while-loop)
            - [Syntax](#syntax)
            - [Example](#example)
            - [Do-While Loop](#do-while-loop)
            - [Syntax](#syntax)
            - [Example](#example)
        - [Loop Control Statements](#loop-control-statements)
            - [Example using break](#example-using-break)
            - [Example using continue](#example-using-continue)
    - [Try/Catch](#trycatch)
        - [Finally Block (Optional)](#finally-block-optional)

<!-- /TOC -->

---

## Basics of JavaScript Syntax: Variables, Data Types, Operators, and Try/Catch

A quick refresher on the basic syntax of JS.

### Variables

Variables are containers for storing data values in JavaScript. They are declared using keywords like var, let, or const.

```js
// Variable declaration and initialization
var age = 25;
let name = 'John';
const PI = 3.14;

// Variable reassignment
age = 30;
```

#### Guidelines

Use `let` and `const` to declare variables with block scope, rather than `var` which has function scope.

This helps in preventing unintended variable hoisting and reduces the risk of variable conflicts or unintended side effects.

Use `const` for variables that are not intended to be reassigned after initialization

### Data Types

JavaScript has several primitive data types, including strings, numbers, booleans, null, undefined, and symbols. It also has complex data types like objects and arrays.

```js
// Primitive data types
let message = 'Hello'; // string
let quantity = 10; // number
let isTrue = true; // boolean
let nothing = null; // null
let notDefined; // undefined

// Complex data types
let person = { name: 'John', age: 30 }; // object
let colors = ['red', 'green', 'blue']; // array
```

### Operators

JavaScript supports various operators for performing operations on data, including arithmetic, assignment, comparison, logical, and more.

```js
// Arithmetic operators
let x = 10;
let y = 5;
let sum = x + y;
let difference = x - y;
let product = x * y;
let quotient = x / y;
let remainder = x % y;

// Assignment operators
let z = 5;
z += 3; // equivalent to z = z + 3

// Comparison operators
let isEqual = x === y;
let isGreater = x > y;

// Logical operators
let andResult = (x > 0) && (y > 0);
let orResult = (x > 0) || (y > 0);
```
---

## Control Flow - if Statements, switch Statements, and Ternary Operators

### If Statements
`if` statements are used to make decisions in code based on a condition.

```js
if (condition) {
    // code block to execute if condition is true
} else {
    // code block to execute if condition is false
}
```

##### Example
```js
let temperature = 25;
if (temperature > 30) {
    console.log("It's a hot day!");
} else if (temperature >= 20 && temperature <= 30) {
    console.log("It's a nice day.");
} else {
    console.log("It's a cold day.");
}
```

### Switch Statements

`switch` statements are used to perform different actions based on different conditions.

```js
switch (expression) {
    case value1:
        // code block to execute if expression matches value1
        break;
    case value2:
        // code block to execute if expression matches value2
        break;
    default:
        // code block to execute if expression doesn't match any case
}
```

#### Example
```js
let day = 'Monday';
switch (day) {
    case 'Monday':
        console.log("It's Monday!");
        break;
    case 'Tuesday':
        console.log("It's Tuesday!");
        break;
    default:
        console.log("It's neither Monday nor Tuesday.");
}
```

### Ternary Operator:

The ternary operator `(? :)` is a concise way of writing `if...else` statements.

#### Syntax
`condition ? expression1 : expression2`

#### Example
```js
let age = 20;
let message = age >= 18 ? 'You are an adult' : 'You are a minor';
console.log(message);
```

## Loops - for Loop, while Loop, do-while Loop, and Loop Control Statements

### For Loop

A for loop is used to execute a block of code repeatedly for a fixed number of times.

#### Syntax
```js
for (initialization; condition; increment/decrement) {
    // code block to execute
}
```

#### Example
```js
for (let i = 0; i < 5; i++) {
    console.log("Iteration " + (i + 1));
}
```

### While Loop

A while loop is used to execute a block of code repeatedly as long as a condition is true.

#### Syntax
```js
while (condition) {
    // code block to execute
}
```

#### Example
```js
let i = 0;
while (i < 5) {
    console.log("Iteration " + (i + 1));
    i++;
}
```

#### Do-While Loop

A do-while loop is similar to a while loop, but it always executes the code block at least once, even if the condition is false.

#### Syntax
```js
do {
    // code block to execute
} while (condition);
```

#### Example
```js
let i = 0;
do {
    console.log("Iteration " + (i + 1));
    i++;
} while (i < 5);
```

### Loop Control Statements

Loop control statements are used to alter the normal flow of loop execution.
Common loop control statements include break and continue.

#### Example using break
```js
for (let i = 0; i < 10; i++) {
    if (i === 5) {
        break; // exit the loop if i equals 5
    }
    console.log("Iteration " + (i + 1));
}
```

#### Example using continue
```js
for (let i = 0; i < 5; i++) {
    if (i === 2) {
        continue; // skip the rest of the loop body if i equals 2
    }
    console.log("Iteration " + (i + 1));
}
```

---

## Try/Catch

In JavaScript, the try and catch statements are used for error handling, allowing you to gracefully handle exceptions (errors) that occur within a block of code. 

The `try` statement is used to enclose the code that you want to monitor for errors. If an error occurs within the try block, JavaScript will stop executing the code in the try block and jump to the catch block.

```js
try {
    // Code that may throw an error
} catch (error) {
    // Code to handle the error
}
```

The `catch` statement follows the `try` block and contains the code that handles the error. If an error occurs within the `try` block, JavaScript will jump to the `catch` block and execute the code inside it. The `catch` block takes one parameter, `error`, which represents the error object thrown by the try block.

Inside the `catch` block, you can write code to handle the error in any way you see fit. This might involve logging the error to the console, displaying an error message to the user, or taking some other action to recover from the error.

### Finally Block (Optional)
In addition to `try` and `catch`, you can also use a `finally` block, which follows the `try` and `catch` blocks and is executed regardless of whether an error occurs. The `finally` block is useful for cleanup tasks that need to be performed, such as closing resources or releasing memory.

```js
try {
    // Code that may throw an error
} catch (error) {
    console.error('An error occurred:', error);
} finally {
    // Code that is always executed
}
```

Here's a complete example demonstrating the use of try and catch:

```js
try {
    // Code that may throw an error
    const result = 10 / 0; // This will throw a division by zero error
    console.log('Result:', result);
} catch (error) {
    // Code to handle the error
    console.error('An error occurred:', error);
}
```
---

[Chapter 2 - Functions & Scope >> ](chapter2.md)