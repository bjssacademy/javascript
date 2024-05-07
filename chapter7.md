# Chapter 7 - Modules 

In ES6, modules provide a way to organize and structure JavaScript code into reusable units of functionality, rather than in one large script. 

Modules allow us to encapsulate variables, functions, classes, or any other code, and selectively *export* them for use in other modules.

## Syntax

To create a module, you typically create a JavaScript file with the code you want to encapsulate. You can then export specific *pieces* of functionality using the `export` keyword and import them into other modules using the `import` keyword.

### Exporting

Create a new file, `math.js`.

```js
// math.js
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

Here we the `add` and `subtract` functions are exported from the `math.js` module, meaning they are available to be imported and used in another module, promoting reuse and separation of concern.

### Importing

Create a new file, `app.js`.

```js
// app.js
import { add, subtract } from './math.js';

console.log(add(5, 3)); // Output: 8
console.log(subtract(5, 3)); // Output: 2
```

In `app.js`, we *import* `add` and `subtract` functions from the `math.js` module and use them in our code.

### Default Exports
You can also export a `default value` from a module, which can be anything: a function, a class, an object, etc.

```js
// math.js
export default function add(a, b) {
  return a + b;
}
```

```js
// app.js
import add from './math.js';

console.log(add(5, 3)); // Output: 8
```

## Default vs Explicit Export

With explicit exports, you specify exactly which variables, functions, or classes you want to export from a module.

With default exports, you export a single value (which can be a function, a class, an object, etc.) as the default export from a module. This means that when you import the module, you can choose any name for the imported value.

### When to Use Each
**Explicit Export**

Use explicit exports when you want to export multiple values from a module and want to specify exactly which values should be imported into other modules. This is useful when you have multiple functions, variables, or classes that you want to export and use separately in other modules.

**Default Export**

Use default exports when you want to export a single value from a module, typically representing the main functionality of the module. Default exports are convenient when you have a primary function, class, or object that you want to export, and you don't want to specify its name when importing it into other modules.

#### Guidelines

- If your module has only *one* thing to export, consider using default export.
- If your module has *multiple* things to export, or if you need to have named exports alongside a default export, use explicit exports.

## Exporting - Public vs Private

Whilst modules don't have an explicit `private` or `public` keyword, you can think of exporting a function, variable or whatever as the difference between making something public (exporting), and private (only available inside the module itself.)

When you use export to export a variable, function, or class from a module, you make it accessible for use in other modules. These exported items are like the public interface of the module, and other modules can import and use them as needed.

On the other hand, variables, functions, or classes that are not exported from a module remain private to that module. They are not accessible from outside the module, and other modules cannot import or use them directly. This encapsulation helps in keeping the module's internal implementation details hidden and prevents unintentional modifications or conflicts.

---

## Tasks

1. Using the previous ES6-updated code, refactor so that the `Animal`, `Dog` and `Cat` classes are in separate modules with the correct exports. 

2. Then import them into your `app.js` file and ensure you can still instantiate them as objects and make them "speak".

---