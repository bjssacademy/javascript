# Chapter X - Manipulating the DOM

The Document Object Model (DOM) is a *programming interface* for web documents. It represents the structure of HTML or XML documents as a hierarchical tree-like structure, where each *node* in the tree corresponds to a part of the document. 

The DOM provides a way to interact with and manipulate the content and structure of web documents dynamically.

The DOM represents a web document as a tree structure, where each node in the tree corresponds to an element, attribute, or text node in the document. The topmost node in the tree is the document node, which represents the entire document.

There are different types of nodes in the DOM tree, such as element nodes, attribute nodes, text nodes, comment nodes, etc. Element nodes represent HTML elements like `<div>`, `<p>`, `<span>`, etc., while text nodes represent the text content within elements.

With the DOM, you can access and manipulate nodes in the document dynamically using JavaScript. This includes adding, removing, or modifying elements and their attributes, changing text content, and handling events.

You can traverse (big words,  maybe "move around" is better) the DOM tree to navigate between nodes. For example, you can move from parent nodes to child nodes, or from sibling nodes to adjacent nodes.

The DOM allows you to attach event listeners to nodes, enabling you to respond to user interactions like clicks, mouse movements, key presses, etc.

Since the DOM represents the document structure as an object model, you can dynamically update the content and structure of the document in response to user actions, data changes, or other events.

## Accessing and manipulating DOM elements

There are several methods and properties provided by the DOM API to facilitate accessing elements. We can "get" elements from the DOM using their tag or attribute values. 

For this, we'll need to create an `index.html` file with this content:

```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Manipulation Example</title>
    <style>
        .highlight {
            background-color: yellow;
        }
    </style>
</head>
<body>

<div id="myElement" class="myClass" changeable-attr="1">Hello, world!</div>

</body>
</html>
```

Open the file in a browser (Chrome is preferred) and run the commands from the DevTools Console to see them in action.

### `getElementById`

This method allows you to access an element in the document by its unique ID. It returns the first element that matches the specified ID. To prove it actually works, we're logging out the text

```js
let element = document.getElementById('myElement');
console.log(element.innerText);
```

### `getElementsByClassName`

This method returns an array of elements that have the specified class name.
```js
// Get elements by class name
let elements = document.getElementsByClassName('myClass');
console.log(elements[0].innerText);
```

### `querySelector`

This method allows you to select the first element that matches a specified CSS selector.

```js
// Query selector
let element = document.querySelector('#myElement .myClass');
console.log(element.innerText);
```

### querySelectorAll

Similar to `querySelector`, but it returns a NodeList containing all elements that match the specified selector.

```js
// Query selector all
let elements = document.querySelectorAll('.myClass');
console.log(elements[0].innerText);
```

## Modifying element attributes, styles, and content

Once you have selected an element or elements, you can manipulate them in various ways.

### Modifying Attributes

You can access and modify element attributes using the `setAttribute` and `getAttribute` methods or by directly accessing the attributes property.
```js
// Set attribute
let element = document.getElementById('myElement');
element.setAttribute('changeable-attr', '5');

// Get attribute
let id = element.getAttribute('changeable-attr');
console.log(id);
```

### Modifying Styles
You can change the inline styles of an element using the style property.

```js
// Modify styles
element.style.color = 'red';
element.style.fontSize = '16px';
```

### Modifying Content

You can change the content of an element using properties like `textContent`, `innerHTML`, or `innerText`.

```js
// Modify content
element.textContent = 'New text content';
element.innerHTML = '<b>New HTML content</b>';
```