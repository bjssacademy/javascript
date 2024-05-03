# Destructuring assignment and spread/rest operators

## Destructuring Assignment
Destructuring assignment allows you to extract values from arrays or properties from objects into distinct variables, making it easier to work with complex data structures.

### Array Destructuring
```js
// Array with two elements
const colors = ['red', 'blue'];

// Destructuring assignment
const [firstColor, secondColor] = colors;

console.log(firstColor);  // Output: 'red'
console.log(secondColor); // Output: 'blue'
```

### Object Destructuring

```js
// Object with properties
const person = {
    name: 'John',
    age: 30
};

// Destructuring assignment
const { name, age } = person;

console.log(name); // Output: 'John'
console.log(age);  // Output: 30
```

## Spread Operator
The spread operator *(...) *allows you to expand elements of an iterable (like an array) into individual elements, or to merge properties of objects.

### Array Spread

```js
const numbers = [1, 2, 3];
const moreNumbers = [...numbers, 4, 5];

console.log(moreNumbers); // Output: [1, 2, 3, 4, 5]
```

### Object Spread
```js
const person = {
    name: 'John',
    age: 30
};

const newPerson = {
    ...person,
    city: 'New York'
};

console.log(newPerson); // Output: { name: 'John', age: 30, city: 'New York' }
```

## Rest Parameter
The rest parameter allows you to represent an *indefinite number of arguments* as an array, simplifying function definitions and handling variable numbers of parameters.

```js
function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
}

console.log(sum(1, 2, 3, 4, 5)); // Output: 15
```

Here the rest parameter `...numbers` collects all the arguments passed to the `sum` function into an array called `numbers`, allowing us to perform array operations like `reduce` on them.

---

Spread syntax looks *exactly* like rest syntax. In a way, spread syntax is the *opposite* of rest syntax. Spread syntax **"expands"** an array into its elements, while rest syntax **collects multiple elements** and "condenses" them into a single element.