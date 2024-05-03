# Chapter 3 - Working with Arrays

<!-- TOC -->

- [Chapter 3 - Working with Arrays](#chapter-3---working-with-arrays)
    - [Introduction to arrays: creating arrays, accessing elements, and array methods](#introduction-to-arrays-creating-arrays-accessing-elements-and-array-methods)
        
    - [Anonymous Functions](#anonymous-functions)
    - [Iterating over arrays: for loop, forEach method, map method, and filter method](#iterating-over-arrays-for-loop-foreach-method-map-method-and-filter-method)
        
    - [Array methods for manipulation: push, pop, shift, unshift, splice, and slice](#array-methods-for-manipulation-push-pop-shift-unshift-splice-and-slice)
       
    - [Array methods for searching and sorting: indexOf, find, findIndex, sort, and reverse](#array-methods-for-searching-and-sorting-indexof-find-findindex-sort-and-reverse)
       
    - [Multidimensional arrays and nested array methods](#multidimensional-arrays-and-nested-array-methods)
        
    - [About Functional Programming](#about-functional-programming)
    - [The `reduce()` Method](#the-reduce-method)

<!-- /TOC -->

##  Introduction to arrays: creating arrays, accessing elements, and array methods

### Creating Arrays

Arrays in JavaScript are used to store multiple values in a single variable. They can hold elements of any data type, including strings, numbers, booleans, objects, or even other arrays.

```js
// Creating an array with square brackets
let colors = ['red', 'green', 'blue'];

// Creating an array using the Array constructor
let numbers = new Array(1, 2, 3, 4, 5);

// An array can hold elements of different data types
let mixedArray = ['apple', 10, true, {name: 'John'}, ['a', 'b', 'c']];
```

### Accessing Elements

Individual elements in an array are accessed using zero-based index notation. You can access elements by their index position within the array.

```js
let colors = ['red', 'green', 'blue'];

console.log(colors[0]); // Output: red
console.log(colors[1]); // Output: green
console.log(colors[2]); // Output: blue

// Accessing the length of the array
console.log(colors.length); // Output: 3
```

### Array Methods

JavaScript provides a variety of built-in methods for working with arrays, such as adding or removing elements, searching for elements, iterating over elements, and more.

```js
let fruits = ['apple', 'banana', 'orange'];

// Adding elements to the end of the array
fruits.push('grape', 'mango'); // ['apple', 'banana', 'orange', 'grape', 'mango']

// Removing the last element from the array
let lastFruit = fruits.pop(); // 'mango'

// Adding elements to the beginning of the array
fruits.unshift('strawberry'); // ['strawberry', 'apple', 'banana', 'orange']

// Removing the first element from the array
let firstFruit = fruits.shift(); // 'strawberry'

// Finding the index of an element
let index = fruits.indexOf('banana'); // 1

// Removing an element by index
let removedFruit = fruits.splice(1, 1); // removes 'banana' from the array

// Iterating over array elements
fruits.forEach(function(fruit) {
    console.log(fruit);
});
```

## Anonymous Functions

We're about to see some *anonymous functions*. So far, you're probably okay with the idea that you can *define* and *call* functions in code.

Well, you can also define functions anonymously. An anonymous function is a function without a name. 

Anonymous functions are declared using the keyword `function()`, and can have zero or more parameters, for example `function(name)` is an anonymous function that accepts one argument.

I'll explain the difference in the `forEach()` method below, and give an example of using an anonymous method vs a named method.

## Iterating over arrays: for loop, forEach method, map method, and filter method

### Using a `for` Loop

A for loop is a traditional way to iterate over arrays. It allows you to loop through each element of the array and perform a specific action on each element.

```js
let numbers = [1, 2, 3, 4, 5];
for (let i = 0; i < numbers.length; i++) {
    console.log(numbers[i]);
}
```

### Using the `forEach()` Method

The `forEach()` method is a built-in method available on arrays that iterates over each element of the array and executes an [anonymous](#anonymous-functions) *[callback function](chapter2.md#callback-functions)* for each element.

```js
let numbers = [1, 2, 3, 4, 5];
numbers.forEach(function(number) {
    console.log(number);
});
```
#### Using a Defined Method

Whilst this code might look a bit odd ad first, here's the equivalent code using a defined/named function as the callback:

```js
// Defined callback function
function logNumber(number) {
    console.log(number);
}

let numbers = [1, 2, 3, 4, 5];

// Using the defined callback function with forEach
numbers.forEach(logNumber);
```

I generally prefer the latter example as it's easier to debug! However, if anonymous functions are being used, you can mentally extract it as a defined method.

### Using the `map()` Method

The `map()` method creates a new array by applying a *[callback function](chapter2.md#callback-functions)* to each element of the original array. It returns a new array with the results of applying the callback function to each element.

```js
let numbers = [1, 2, 3, 4, 5];
let doubledNumbers = numbers.map(function(number) {
    return number * 2;
});
console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
```

#### Using a Defined Method

```js
// Defined method for doubling numbers
function doubleNumber(number) {
    return number * 2;
}

let numbers = [1, 2, 3, 4, 5];

// Using the defined method with map
let doubledNumbers = numbers.map(doubleNumber);

console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
```

### Using the `filter()` Method

The `filter()` method creates a new array with all elements that pass a test implemented by the provided *[callback function](chapter2.md#callback-functions)*.

```js
let numbers = [1, 2, 3, 4, 5];
let evenNumbers = numbers.filter(function(number) {
    return number % 2 === 0;
});
console.log(evenNumbers); // Output: [2, 4]
```

#### Using a Defined Method

```js
// Defined method for filtering even numbers
function isEven(number) {
    return number % 2 === 0;
}

let numbers = [1, 2, 3, 4, 5];

// Using the defined method with filter
let evenNumbers = numbers.filter(isEven);

console.log(evenNumbers); // Output: [2, 4]

```
---

## Array methods for manipulation: push, pop, shift, unshift, splice, and slice

Let's delve deeper into array methods for manipulation in JavaScript, including `push`, `pop`, `shift`, `unshift`, `splice`, and `slice`.

### `push()`

The `push()` method adds one or more elements to the end of an array and returns the new length of the array.

```js
let fruits = ['apple', 'banana', 'orange'];
fruits.push('grape', 'mango');
console.log(fruits); // Output: ['apple', 'banana', 'orange', 'grape', 'mango']
```

### `pop()`

The `pop()` method removes the last element from an array and returns that element. It mutates the original array.

```js
let fruits = ['apple', 'banana', 'orange', 'grape', 'mango'];
let lastFruit = fruits.pop();
console.log(lastFruit); // Output: 'mango'
console.log(fruits); // Output: ['apple', 'banana', 'orange', 'grape']
```

### `shift()`

The `shift()` method removes the first element from an array and returns that element. It mutates the original array.

```js
let fruits = ['apple', 'banana', 'orange', 'grape'];
let firstFruit = fruits.shift();
console.log(firstFruit); // Output: 'apple'
console.log(fruits); // Output: ['banana', 'orange', 'grape']
```

### `unshift()`

The `unshift()` method adds one or more elements to the beginning of an array and returns the new length of the array.

```js
let fruits = ['banana', 'orange', 'grape'];
fruits.unshift('apple', 'mango');
console.log(fruits); // Output: ['apple', 'mango', 'banana', 'orange', 'grape']
```

### `splice()`

The `splice()` method changes the contents of an array by removing or replacing existing elements and/or adding new elements in place.

```js
let fruits = ['apple', 'banana', 'orange', 'grape', 'mango'];
// Remove 'orange' and 'grape', and add 'kiwi' and 'peach' at their position
let removedFruits = fruits.splice(2, 2, 'kiwi', 'peach');
console.log(removedFruits); // Output: ['orange', 'grape']
console.log(fruits); // Output: ['apple', 'banana', 'kiwi', 'peach', 'mango']
```

### `slice()`

The `slice()` method returns a shallow copy of a portion of an array into a new array object selected from start to end (end not included). The original array will not be modified.

```js
let fruits = ['apple', 'banana', 'orange', 'grape', 'mango'];
let selectedFruits = fruits.slice(1, 4); // Get elements from index 1 to 3
console.log(selectedFruits); // Output: ['banana', 'orange', 'grape']
console.log(fruits); // Output: ['apple', 'banana', 'orange', 'grape', 'mango']
```

## Array methods for searching and sorting: indexOf, find, findIndex, sort, and reverse

Methods such as `indexOf`, `find`, `findIndex`, `sort`, and `reverse` are useful for searching and sorting arrays in JavaScript.

### `indexOf()`

The `indexOf()` method returns the first index at which a specified element is found in the array, or -1 if the element is not found.

```js
let fruits = ['apple', 'banana', 'orange', 'banana', 'mango'];
let index = fruits.indexOf('banana');
console.log(index); // Output: 1 (index of the first occurrence of 'banana')
```

### `find()`

The `find()` method returns the value of the first element in the array that satisfies the provided testing function, or undefined if no such element is found.

```js
let numbers = [10, 20, 30, 40, 50];
let foundNumber = numbers.find(function(number) {
    return number > 25;
});
console.log(foundNumber); // Output: 30 (the first number greater than 25)
```

### `findIndex()`

The `findIndex()` method returns the index of the first element in the array that satisfies the provided testing function, or -1 if no such element is found.

```js
let numbers = [10, 20, 30, 40, 50];
let index = numbers.findIndex(function(number) {
    return number > 25;
});
console.log(index); // Output: 2 (the index of the first number greater than 25)
```

### `sort()`

The `sort()` method sorts the elements of an array in place and returns the sorted array. By default, the elements are sorted as strings.

```js
let fruits = ['orange', 'apple', 'banana', 'mango'];
fruits.sort();
console.log(fruits); // Output: ['apple', 'banana', 'mango', 'orange'] (sorted alphabetically)
```

### `reverse()`

The `reverse()` method reverses the order of the elements in an array in place and returns the reversed array.

```js
let numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers); // Output: [5, 4, 3, 2, 1] (reversed order)
```

## Multidimensional arrays and nested array methods

### Multidimensional Arrays

A *multidimensional array* is an array of arrays, where each element of the outer array is itself an array. This allows for the creation of grids, matrices, or collections of data organized in rows and columns.

#### Example

```js
let grid = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];
```

In this example, `grid` is a 2-dimensional array with 3 rows and 3 columns.

### Nested Array Methods

Nested array methods are array methods that can be applied to multidimensional arrays. These methods can iterate over the *outer* array and apply *another* array method to each *inner* array, enabling operations on all elements of the multidimensional array.

> NOTE: We're about to use some very funky programming, known as [functional programming](#about-functional-programming). Functional programming is a programming paradigm, so the code below looks extremely clean, but is actually quite complex to understand.
>
> JavaScript is a multi-paradigm language, meaning it supports multiple programming paradigms, including functional programming. While JavaScript is not strictly a functional programming language like Haskell or Lisp, it does provide many features and capabilities that align with the principles of functional programming.
> 
> We'll explain more in the next section and compare using these methods to using for loops.

#### Example

Let's say we have a 2-dimensional array representing a grid of numbers, and we want to calculate the sum of all numbers in the grid.

```js
let grid = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

// Using nested array methods to calculate the sum
//DO NOT WORRY THAT THIS MAKES NO SENSE RIGHT NOW!
let sum = grid.map(row => row.reduce((acc, val) => acc + val, 0)).reduce((acc, val) => acc + val, 0);

console.log(sum); // Output: 45 (sum of all numbers in the grid)
```

Let's examine what's going on here.

1. We use the [map()](#using-the-map-method) method to iterate over each row of the grid.
2. For each row, we use the [reduce()](#the-reduce-method) method to calculate the sum of numbers in that row.
3. Finally, we use another [reduce()](#the-reduce-method) method to calculate the sum of all row sums, giving us the total sum of all numbers in the grid.


### Common Nested Array Methods:

- `map()` and `forEach()` to iterate over each element (array) in the outer array and apply another array method to each inner array.
- `filter()` to filter elements in the outer array based on a condition, possibly involving operations on each inner array.
- `reduce()` to reduce the multidimensional array to a single value, possibly by aggregating values from each inner array.

---

## About Functional Programming

Whilst JS isn't strictly a functional programming language, lots of the methods we have discussed are *higher-order functions* that enable functional-style programming.

Functional programming has a *declarative* style where the focus is on describing *what* should be done rather than *how* it should be done.

`map()` encourages a declarative programming approach. Instead of manually iterating over the array and modifying each element, you simply provide a transformation function as an argument to `map()`. This function describes how each element should be transformed, rather than specifying the exact steps needed to achieve the transformation.

Looking at our example above using the method `reduce()` (which frankly made my head explode the first time I saw it), you can actually do the same thing in an *imperative* style without using `reduce()` at all:

```js
let grid = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
];

let sum = 0;

// Loop over each row
for (let i = 0; i < grid.length; i++) {
    // Loop over each element in the row
    for (let j = 0; j < grid[i].length; j++) {
        // Add the current element to the sum
        sum += grid[i][j];
    }
}

console.log(sum); // Output: 45

```

## The `reduce()` Method

The `reduce()` method in JavaScript is used to..er..reduce the elements of an array to a single value. It executes a provided callback function once for each element in the array, resulting in a single output value. 

The `reduce()` method takes two main parameters: the reducer function and an initial value (optional). The reducer function accepts four arguments: accumulator, currentValue, currentIndex, and the array itself.

Here's how the `reduce()` method works.

1. The reducer function is applied to each element of the array sequentially.
2. It takes the accumulator (the result of the previous iteration) and the current element (currentValue) as arguments.
3. The return value of the reducer function becomes the new accumulator value for the next iteration.
4. The initial value (if provided) serves as the initial value of the accumulator in the first iteration.

Now, let's see an example of using `reduce()` to find the sum of elements in an array

```js
let numbers = [1, 2, 3, 4, 5];

// Using reduce() to calculate the sum of elements
let sum = numbers.reduce(function(accumulator, currentValue) {
    return accumulator + currentValue;
}, 0);

console.log(sum); // Output: 15 (1 + 2 + 3 + 4 + 5)
```

- We start with an array of numbers `[1, 2, 3, 4, 5]`.
- The reducer function takes two arguments: `accumulator` (initialized to 0) and `currentValue` (each element of the array).
- In each iteration, the reducer function adds the current element (`currentValue`) to the accumulator.
- Finally, the `reduce()` method returns the accumulated sum of all elements in the array.

> Using an initial value of 0 (`reduce(0)`) ensures that if the array is empty, the result of the reduction will be 0. If you don't provide an initial value and the array is empty, `reduce()` will throw an error.

So `reduce()` can be used for various operations like summing values, calculating averages, flattening arrays, grouping elements, and more

---

If your brain is hurting right now, don't worry, that's pretty normal. I'll be using a more imperative style where possible, but you will see `map()` used a few times, and I'll avoid the use of `reduce()`!

---

[Chapter 4 - Working with Objects](#chapter4.md)