# ES6

ES6, also known as *ECMAScript 2015*, brought significant enhancements to JavaScript, introducing new syntax and features to make code more expressive and readable.

Here we will highlight some of them.

## 1. `let` and `const`

`let` allows *block-scoped* variables while `const` declares constants that can't be re-assigned.

```js
let x = 10;
const PI = 3.14;
```

## 2. Arrow Functions

A concise syntax for writing *anonymous* functions.

```js
const add = (a, b) => a + b;
```

## 3. Template Literals

Allow embedding expressions inside strings using backticks.

```js
const name = "Alice";
console.log(`Hello, ${name}!`);
```

## 4. Classes

Syntactical sugar over JavaScript's existing prototype-based inheritance.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog('Rex');
dog.speak(); // Output: "Rex barks."
```

### Class Declaration:
To declare a class, you use the class keyword followed by the name of the class. 

```js
class ClassName {
  // Class body
}
```

### Constructor Method
The constructor method is a special method that gets called when you create a new instance of a class using the new keyword. It's used for initializing object properties or performing any setup required for the object.

```js
class ClassName {
  constructor(/* parameters */) {
    // Initialize properties or perform setup
  }
}
```

### Class Methods
You can define methods inside the class body just like regular functions, except they are methods of the class. These methods can be called on instances of the class.

```js
class ClassName {
  constructor(/* parameters */) {
    // Initialize properties or perform setup
  }

  methodName() {
    // Method logic
  }
}
```

### Inheritance
You can create a subclass (or derived class) that inherits from a superclass (or base class) using the extends keyword. The subclass can override methods or add new methods to customize its behaviour.

```js
class SubClassName extends SuperClassName {
  constructor(/* parameters */) {
    super(/* arguments to pass to superclass constructor */);
    // Initialize subclass properties or perform setup
  }

  // Subclass-specific methods
}
```

### `super` Keyword
Within a subclass constructor, you use the `super` keyword to call the constructor of the superclass. This is necessary to initialize properties defined in the superclass and perform any setup logic defined in the superclass constructor.

### Usage
Once you've defined a class, you can create instances of that class using the `new` keyword.

```js
const instance = new ClassName(/* arguments for constructor */);
```

## 5. Modules

Allows splitting code into multiple files and importing/exporting functionality between them.

```js
// math.js
export const add = (a, b) => a + b;

// app.js
import { add } from './math.js';
console.log(add(2, 3)); // Output: 5
```

## 6. Destructuring

Easily extract values from arrays or objects into variables.

```js
const person = { name: 'Alice', age: 30 };
const { name, age } = person;
console.log(name, age); // Output: Alice 30
```

## 7. Spread and Rest Operators
`...` can be used to spread elements of an iterable like arrays or objects, or to collect them into a single variable.

```js
// Spread operator
const arr = [1, 2, 3];
const newArr = [...arr, 4, 5]; // Output: [1, 2, 3, 4, 5]

// Rest parameter
const sum = (...args) => args.reduce((acc, val) => acc + val, 0);
console.log(sum(1, 2, 3, 4)); // Output: 10
```

## 8. Default Parameters

Allows you to specify default values for function parameters.

```js
const greet = (name = 'World') => {
  console.log(`Hello, ${name}!`);
};

greet(); // Output: Hello, World!
greet('Alice'); // Output: Hello, Alice!
```

## 9. Promises

Provides a cleaner alternative to callbacks for handling asynchronous operations.

```js
const fetchData = () => {
  return new Promise((resolve, reject) => {
    // Simulating async data fetching
    setTimeout(() => {
      resolve('Data fetched successfully!');
    }, 2000);
  });
};

fetchData()
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

## 10. Symbol

Introduces a new primitive data type for unique object keys.

```js
const uniqueKey = Symbol('unique');
const obj = {
  [uniqueKey]: 'value'
};

console.log(obj[uniqueKey]); // Output: value
```

## 11. Iterators and Generators

Provides a way to define custom iteration behavior for objects.

```js
const myIterable = {
  *[Symbol.iterator]() {
    yield 1;
    yield 2;
    yield 3;
  }
};

for (const value of myIterable) {
  console.log(value);
}
// Output:
// 1
// 2
// 3
```