# Chapter 4 - Working with Objects

In JavaScript (and many other languages), objects are fundamental data structures used to store collections of key-value pairs. Objects can represent complex data structures and are used extensively to model real-world entities and concepts. 

Objects allow us to organise related data into a single entity - that is, we can keep data about one thing together and pass the object around rather than having to pass all the variables it contains.

Imagine I was an estate agent with two houses to sell. They have important information like number of bedrooms, bathrooms etc. My code might look like:

```js
house1_bedrooms = 4
house1_bathrooms = 2

house2_bedrooms = 3
house2_bathrooms = 1
```

Well, this is a bit odd. I want to refer to the *house* not the exact *property variable*. I can't for instance sort the data by the number of bedrooms without knowing the exact name of each variable that contains that information.

I could code it:

```js
if (house1_bedrooms > house2_bedrooms){
    console.log("House has " + house1_bedrooms + " bedrooms and " + house1_bathrooms + "  bathrooms.")
} else {
    console.log("House has " + house2_bedrooms + " bedrooms and " + house2_bathrooms + "  bathrooms.")
}
```

But what if I have 3 houses? Or 10? Or 1000?

This is where objects come in. Instead of writing explicit variables, we can encapsulate that data together in an object.

```js
function House(bedrooms, bathrooms) {
    this.bedrooms = bedrooms;
    this.bathrooms = bathrooms;
}

let houses = [
    new House(4, 2),
    new House(3, 1)
];

// Sort houses by number of bedrooms
houses.sort((a, b) => b.bedrooms - a.bedrooms);

// Print the house with the highest number of bedrooms
let houseWithMostBedrooms = houses[0];

console.log("House has " + houseWithMostBedrooms.bedrooms + " bedrooms and " + houseWithMostBedrooms.bathrooms + "  bathrooms.")

```

Don't worry if that code doesn't make sense just yet! We're going to go through it in the next few sections. Just know that objects are used to keep associated data together for the same type of things. Here, our object is a house, which has various properties (bedrooms, bathrooms) that are always the same between all instances of house.

---
<!-- TOC -->


- [Introduction to objects: creating objects, accessing properties, and object methods](#introduction-to-objects-creating-objects-accessing-properties-and-object-methods)
       
- [Functions vs Methods](#functions-vs-methods)
- [Object literals vs. object constructors](#object-literals-vs-object-constructors)
       
- [Working with object properties: adding, updating, and deleting properties](#working-with-object-properties-adding-updating-and-deleting-properties)
     
- [Object-Oriented Programming Concepts: Encapsulation, Inheritance, and Polymorphism](#object-oriented-programming-concepts-encapsulation-inheritance-and-polymorphism)
        
- [Object Prototype](#object-prototype)

<!-- /TOC -->
---

## Introduction to objects: creating objects, accessing properties, and object methods

Objects in JavaScript are versatile *data structures* used to represent key-value pairs. They can store various types of data, including primitives, arrays, and even other objects.

### Creating Objects

Objects in JavaScript can be created using *object literals* `{}` or the `new Object()` constructor.

#### Using object literals

```js
// Object literal syntax
let person = {
    name: 'John', //<- this is a property called `name` with the value of `John`
    age: 30, //<- this is a property called `age` with the value of 30
    city: 'New York' //<- this is a property called `city` with the value of `New York`
};

console.log(person)
```

### Accessing Properties

Properties of an object can be accessed using dot notation (`object.property`) or bracket notation (`object['property']`).

```js
console.log(person.name); // Output: 'John'
console.log(person['age']); // Output: 30
```

### Object Methods

In JavaScript, objects can also contain *methods*, which are functions stored as object properties.

```js
let person = {
    name: 'John',
    age: 30,
    greet: function() {
        console.log('Hello, my name is ' + this.name + ' and I am ' + this.age + ' years old.');
    }
};

person.greet(); // Output: 'Hello, my name is John and I am 30 years old.'
```
Here `greet` is a *method* of the `person` *object*. 

It's defined as a *function* that logs a greeting message using the name and age properties of the person object. 

## Functions vs Methods

Methods and functions are blocks of reusable code that perform a specific task. However, there are some key differences between them.

- Functions are standalone blocks of code, while methods *are* functions that are *associated with objects*.
- Functions can be invoked independently, while methods are invoked on objects using dot or bracket notation.
- Methods have access to the object they are attached to via the this keyword, while functions do not have inherent access to any specific object.
- Both functions and methods are used for encapsulating reusable blocks of code, but methods are typically used when the behavior is closely related to the object's state or properties.

> So....methods *are* functions, but they are called *methods* when the functions is part of an *object*.

Don't worry, you'll get used to it.

---

## Object literals vs. object constructors

### Object Literals

Object literals are a simple and concise way to create objects directly. They allow you to define and initialize an object in a single statement, using curly braces `{}`.

```js
// Object literal syntax
let person = {
    name: 'John',
    age: 30,
    greet: function() {
        console.log('Hello, my name is ' + this.name + ' and I am ' + this.age + ' years old.');
    }
};

person.greet()
```

- Simple and concise syntax using curly braces `{}`.
- Best suited for creating individual objects with unique properties.
- Cannot be easily reused to create multiple similar objects.

### Object Constructors

Object constructors are functions used to create multiple instances of objects with similar properties and methods. You define a constructor function and then create new instances of the object using the new keyword.

```js
// Object constructor function
function Person(name, age) {
    this.name = name;
    this.age = age;
    this.greet = function() {
        console.log('Hello, my name is ' + this.name + ' and I am ' + this.age + ' years old.');
    };
}

// Creating instances using the constructor function
let person1 = new Person('John', 30);
let person2 = new Person('Alice', 25);

person1.greet()
person2.greet()

```

- Uses constructor functions to define object blueprints.
- Allows for creating multiple instances of objects with shared properties and methods.
- Provides a convenient way to encapsulate object creation logic and behavior.

### Which One Do I Use?

Use object literals when you need to create a *single, unique object with specific properties and methods*.

Use object constructors when you need to create multiple instances of objects with similar properties and methods, or when you want to encapsulate object creation logic and behaviour.

So, if you have a one-off need for an object, you can use an object literal - maybe something like configuration.

However, if you have multiple different instances - for example if we had 500 people in a database - we would use an object constructor.

---

## Working with object properties: adding, updating, and deleting properties

### Adding Properties

You can add new properties to a JavaScript object by simply assigning a value to a new property name.

```js
let person = {
    name: 'John',
    age: 30
};

// Adding a new property
person.city = 'New York';

console.log(person); // Output: { name: 'John', age: 30, city: 'New York' }
```

### Updating Properties

You can update existing properties of an object by assigning a new value to an existing property name.

```js
let person = {
    name: 'John',
    age: 30
};

// Updating an existing property
person.age = 35;

console.log(person); // Output: { name: 'John', age: 35 }
```

### Deleting Properties

You can delete properties from an object using the `delete` operator.

```js
let person = {
    name: 'John',
    age: 30
};

// Deleting a property
delete person.age;

console.log(person); // Output: { name: 'John' }
```

---

##  Object Methods and this Keyword

In JavaScript, we now know that methods are functions that are properties of objects. These methods allow objects to perform actions or computations (or in our case print something out). But how do we access the properties of the object *inside the object*? We use the `this` keyword:

```js
let person = {
    name: 'John',
    age: 30,
    greet: function() {
        console.log('Hello, my name is ' + this.name + ' and I am ' + this.age + ' years old.');
    }
};

person.greet(); // Output: 'Hello, my name is John and I am 30 years old.'
```

### this Keyword

The `this` keyword refers to the *current* object, allowing you to access properties and methods within the object's scope. It allows methods to access and operate on the object's own properties.

## Object-Oriented Programming Concepts: Encapsulation, Inheritance, and Polymorphism

### Encapsulation

Encapsulation is the bundling of data and methods that operate on the data into a single unit (an object). This concept allows you to *hide* the internal state of an object and only expose methods for interacting with the object's state.

Encapsulation, also known as information hiding, is a fundamental concept in object-oriented programming (OOP). It refers to the practice of restricting *direct* access to certain components or details of an object's implementation, while exposing only the essential interfaces or behaviors necessary for interacting with the object.

In JavaScript, information hiding is typically achieved by defining properties and methods as private or public. Private members are only accessible within the object itself, while public members are accessible from outside the object.

Let's consider our person code again:

```js
// Example of encapsulation
function Person(name, age) {
    this.name = name;
    this.age = age;

    this.greet = function() {
        console.log('Hello, my name is ' + this.name + ' and I am ' + this.age + ' years old.');
    };
}

let person = new Person('John', 30);
person.greet(); // Output: 'Hello, my name is John and I am 30 years old.'
```

This object doesn't *really* encapsulate the properties within it if they are not supposed to be editable. This is because we can *directly* modify the `name` and `age` of the person after we create the object:

```js
// Directly accessing and modifying properties
console.log('Before modification:', person.name, person.age); // Output: 'Before modification: John 30'
person.name = 'Alice';
person.age = 25;
console.log('After modification:', person.name, person.age); // Output: 'After modification: Alice 25'
person.greet(); // Output: 'Hello, my name is Alice and I am 25 years old.'
```

To ensure encapsulation we provide access only through public methods:

```js
function Person(name, age) {
    // Private variables
    let _name = name;
    let _age = age;

    // Private method
    function getAge() {
        return _age;
    }

    // Public method (privileged method)
    this.getName = function() {
        return _name;
    };

    // Public method accessing private method
    this.getInfo = function() {
        return _name + ' is ' + getAge() + ' years old.';
    };
}

let person = new Person('John', 30);

// Accessing public method to get the name
console.log(person.getName()); // Output: 'John'

// Attempting to access private variable directly (will result in undefined)
console.log(person._name); // Output: undefined

// Accessing public method to get the information
console.log(person.getInfo()); // Output: 'John is 30 years old.'
```

### Inheritance

Inheritance is a mechanism in object-oriented programming where a new class (*subclass*) can inherit properties and methods from another class (*superclass*). 

Inheritance allows us to create a blueprint of common things shared by different instances. For instance, we might write some code for a Dog and a Cat:

```js
// Define Dog object
function Dog(name) {
    this.name = name,
    this.species = 'Dog',
    this.sound = function() {
        console.log(this.name + ' the ' + this.species + ' makes a sound.');
    }
};

// Define Cat object
function Cat(name) {
    this.name = name,
    this.species = 'Cat',
    this.sound = function() {
        console.log(this.name + ' the ' + this.species + ' makes a sound.');
    }
};

let dog = new Dog('Buddy');

let cat = new Cat('Whiskers');

// Call the sound method on each instance
dog.sound(); // Output: 'Buddy the Dog makes a sound.'
cat.sound(); // Output: 'Whiskers the Cat makes a sound.'
```

But what we've done here is actually **repeated** ourselves a lot. Both the `Dog` and the `Cat` object have the exact same properties and methods. What if we wanted a Horse? Would we create another object again? That's a lot of code duplication - and worse if we had 100 objects and wanted to add a property, or update a method, we'd have to change it in 100 places!

So we need to find the commonality between Dog and Cat.

Inheritance can be though of as `is a` - for example a Cat `is a` Animal. But so is a Dog.

So if they are both Animals, we can create a *superclass* of Animal that they will inherit from, giving them the same common properties and methods:

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

Now, it may not look like a lot, but now we have our *common* properties in an `Animal` superclass, and our subclasses `Dog` and `Cat` call the `Animal` constructor.

We never call the `Animal` class directly, Instead, when we create a new instance of `Dog` with the argument `Buddy` as the name, our `Dog` class calls the `Animal` constructor passing it the name of the animal and the type (Dog).

Using the `Animal` class in this way allows us to *inherit* all the properties of Animal, whilst allowing flexibility for Dog and Cat separately.

What do I mean by that? Well, let's say we have some new method that all animals share - the ability to move. We can add that as a method on `Animal`:

```js
function Animal(name, species) {
    this.name = name;
    this.species = species;
    this.sound = function() {
        console.log(this.name + ' the ' + this.species + ' makes a sound.');
    };
    this.move = function() {
        console.log(this.name + ' the ' + this.species + ' moves');
    }
}
```

Now we can use that method in `Dog` and `Cat` without writing any extra code:

```js
dog.move(); // Output: 'Buddy the Dog moves.'
cat.move(); // Output: 'Whiskers the Cat moves.
```

And we can also add methods that are special for only `Dog` and not have them for `Cat`. If you throw a ball for a dog, they'll fetch it - try telling a cat to do that...

```js
function Dog(name) {
    Animal.call(this, name, 'Dog');
    this.fetch = function() {
        console.log(this.name + ' the ' + this.species + ' fetches.');
    }
}
```

Now you can do 

```js
dog.fetch(); // Output: 'Buddy the Dog fetches.'
```

But *crucially* the Cat *does not fetch*. If you try:

```js
cat.fetch();
```

You will get an error: `TypeError: cat.fetch is not a function`

That's because `fetch` is *only* a method available on the `Dog` object. In this way, using inheritance, you can share common properties or methods, whilst having separate methods that are explicit for the subclass (also sometimes known as the concrete class).

### Polymorphism

Polymorphism is a fundamental concept in object-oriented programming that allows objects of different classes to be treated as objects of a common superclass. It enables you to use objects of different classes interchangeably. Why? Well, let's look at our previous example:

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

Imagine we had 100 animals. We'd have to write out every single `.sound()` call for each one. But what if we could treat them all the same?

Fortunately, because both `Dag` and `Cat` inherit from the superclass `Animal`, and share the method `sound()`, we can actually use that to our advantage. We can create an array of our objects and iterate through them calling the `sound` method:

```js

//dog.sound(); 
//cat.sound(); 

let animals = [dog, cat];

for (let i = 0; i < animals.length; i++) {
    let animal = animals[i];
    animal.sound(); // Output: Depends on the specific subclass (e.g., 'Buddy the Dog makes a sound.' or 'Whiskers the Cat makes a sound.')
}

// Or, using the forEach with an anonymous function:

animals.forEach(function(animal) {
    animal.sound(); // Output: Depends on the specific subclass (e.g., 'Buddy the Dog makes a sound.' or 'Whiskers the Cat makes a sound.')
});

```

## Object Prototype

In JavaScript, each object has an associated *prototype* object, which acts as a template or blueprint for the object. The prototype object contains properties and methods that are shared among all instances of the object. The prototype property is used to add properties and methods to objects through their prototype chain.

ChatGPT tells me that adding methods to objects should be done using `prototype`:

> Using .prototype allows us to define methods on a function's prototype object, which is shared among all instances created with that constructor function. This approach offers several benefits:
>
>- Memory Efficiency: When methods are defined on the prototype, they are shared among all instances. This means that every instance does not need its own copy of the method, resulting in better memory utilization.
>- Performance: Methods defined on the prototype are only stored once in memory, and all instances share the same method reference. This can lead to better performance compared to defining methods directly within the constructor function, where each instance would have its own copy of the method.
>- Inheritance: When creating subclasses, using .prototype allows for proper prototype chaining. Subclasses can inherit methods from their superclass's prototype chain, ensuring a clean separation of concerns and promoting code reuse.
>- Dynamic Update: Methods defined on the prototype can be dynamically updated or extended at runtime. This means that changes made to the prototype are reflected in all instances and any new instances created afterward.
>
>While it's possible to define methods directly within the constructor function (as properties of this), doing so can lead to inefficiencies, especially when dealing with multiple instances or subclasses. Using `.prototype` offers a cleaner and more efficient way to define methods in JavaScript.

I'm not totally convinced, and I prefer to have my methods enclosed inside my object class. However, in the interest of balance, let's have a look how it would change the code above:

```js
// Define Animal superclass
function Animal(name, species) {
    this.name = name;
    this.species = species;
}

// Common method shared by all animals
Animal.prototype.sound = function() {
    console.log(this.name + ' the ' + this.species + ' makes a sound.');
};

// Define Dog subclass
function Dog(name) {
    Animal.call(this, name, 'Dog');
}

// Set up prototype chain for inheritance
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

// Define Cat subclass
function Cat(name) {
    Animal.call(this, name, 'Cat');
}

// Set up prototype chain for inheritance
Cat.prototype = Object.create(Animal.prototype);
Cat.prototype.constructor = Cat;

// Create instances of Dog and Cat
let dog = new Dog('Buddy');
let cat = new Cat('Whiskers');

// Call the sound method on each instance
dog.sound(); // Output: 'Buddy the Dog makes a sound.'
cat.sound(); // Output: 'Whiskers the Cat makes a sound.'
```

- `Animal.prototype` refers to the prototype object associated with the Animal constructor function.
- `sound` is a method that is being added to the Animal prototype object.
- By adding `sound` to the Animal prototype, all instances created with the Animal constructor function will inherit this method.
- Inside the `sound` method, `this.name` refers to the `name` property of the object that calls the method. This allows the method to access the name property of each individual animal object when it is called.

> I'm still not convinced this is better!

However, there is a time where this makes more sense, and that's normally what we'd call method overriding in other languages. We know dogs bark and cats meow, so if we move the `sound` method down to the subclass we can get more specific. Let's add in a Duck class:

```js
// Define Animal superclass
function Animal(name, species) {
    this.name = name;
    this.species = species;
}

Animal.prototype.sound = function() {
    console.log(this.name + ' the ' + this.species + ' makes a generic sound.');
};

// Define Dog subclass
function Dog(name) {
    Animal.call(this, name, 'Dog');
}
Dog.prototype.sound = function() {
    console.log(this.name + ' the ' + this.species + ' barks.');
};

// Define Cat subclass
function Cat(name) {
    Animal.call(this, name, 'Cat');
}
Cat.prototype.sound = function() {
    console.log(this.name + ' the ' + this.species + ' meows.');
};

// Define Duck subclass
function Duck(name) {
    Animal.call(this, name, 'Duck');
}

// Create instances of Dog and Cat
let dog = new Dog('Buddy');
let cat = new Cat('Whiskers');
let duck = new Duck('Daffy');

dog.sound();
cat.sound();
duck.sound();

```

Which outputs:

```
Buddy the Dog barks.
Whiskers the Cat meows.
Daffy the Duck makes a generic sound.
```

This allows us to have a `fallback` or default `sound` method if the subclass doesn't override it.

---

[Chapter 5 - Asynchronous JavaScript >>](chapter5.md)