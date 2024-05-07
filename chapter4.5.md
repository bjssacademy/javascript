# Chapter 4.5 - Applying ES6


[ES6](es6.md) made significant changes to JS in 2015. Whilst you can still use the objects int he way we showed in the previous chapter (and you will still see examples all over the web), you can actually make your code cleaner and more expressive using ES6 syntax.

One important change is the [way classes are declared and used](es6.md#4-classes). Whilst this still uses prototype under the hood, it's far easier to read.

Let's refactor our last example from Chapter 4 to be ES6.

## Vanilla JS

```js
// Define Animal superclass
function Animal(name, species) {
    this.name = name;
    this.species = species;
    this.sound = function() {
        console.log(this.name + ' the ' + this.species + ' makes a sound.');
    };
}

// Define Dog subclass
function Dog(name) {
    Animal.call(this, name, 'Dog');
}

// Define Cat subclass
function Cat(name) {
    Animal.call(this, name, 'Cat');
}

// Create instances of Dog and Cat
let dog = new Dog('Buddy');
let cat = new Cat('Whiskers');

// Call the sound method on each instance
dog.sound(); // Output: 'Buddy the Dog makes a sound.'
cat.sound(); // Output: 'Whiskers the Cat makes a sound.'
```

## ES6

```js
// Define Animal superclass
class Animal {
  constructor(name, species) {
    this.name = name;
    this.species = species;
  }

  sound() {
    console.log(`${this.name} the ${this.species} makes a sound.`);
  }
}

// Define Dog subclass
class Dog extends Animal {
  constructor(name) {
    super(name, 'Dog');
  }
}

// Define Cat subclass
class Cat extends Animal {
  constructor(name) {
    super(name, 'Cat');
  }
}

// Create instances of Dog and Cat
let dog = new Dog('Buddy');
let cat = new Cat('Whiskers');

// Call the sound method on each instance
dog.sound(); // Output: 'Buddy the Dog makes a sound.'
cat.sound(); // Output: 'Whiskers the Cat makes a sound.'

```

## Changes

### 1. Replaced function declarations with class syntax

#### Before

```js
function Animal(name, species) {
    this.name = name;
    this.species = species;
    this.sound = function() {
        console.log(this.name + ' the ' + this.species + ' makes a sound.');
    };
}
```

#### After

1. Where we previously used the keyword `function` to declare a class, now we use the keyword `class`.

2. We moved the parameters into an explicit `constructor` method.

3. Removed the `this.sound()` function call, and used the new method syntax which is more concise

```js
class Animal {  // 1. replace function with class
  constructor(name, species) { // 2. move parameters into constructor method
    this.name = name;
    this.species = species;
  }

  sound() { // 3. replace with ES6 method syntax
    console.log(this.name + ' the ' + this.species + ' makes a sound.');
  }
}
```

### 2. Inheritance changes

#### Before

```js
function Dog(name) {
    Animal.call(this, name, 'Dog');
}
```

#### After

```js
class Dog extends Animal { // 1. Replace function syntax with class syntax, and used extends keyword
  constructor(name) { //2. moved parameters to constructor
    super(name, 'Dog');
  }
}
```

In the vanilla version, the `Animal` and subclass constructors are defined separately, and the `call` method is used to ensure that the subclass constructor inherits properties from the superclass. 

In the ES6 version, the `extends` keyword is used to establish inheritance, and the `super` keyword is used to call the superclass constructor within the subclass constructor. This syntax is far more common amongst other languages.

### 3. Used string interpolation (`${}`) for string formatting 

[String Interpolation](es6.md#3-template-literals) in Js is achieved using template literals. This makes it easier to see variables and expressions, and makes it easier to maintain your code, and allows for multiline strings.


#### Before

```js
console.log(this.name + ' the ' + this.species + ' makes a sound.');
```

#### After

```js
console.log(`${this.name} the ${this.species} makes a sound.`);
```

---

## Overview

Our usage of the objects hasn't changed, and with the move to ES6 classes we have made it more explicit about what is a class, that the parameters are, and what the methods are.

We've also made it easier to `extend` the class, rather than having the odd `Animal.call()` syntax.

---

[Chapter 5 - Asynchronous JavaScript >>](chapter5.md)