# Introduction

- The Document Object Model, commonly referred to as the DOM, is a programming interface for web documents. 

- It represents the structure of an HTML or XML document as a tree-like structure, where each element, attribute, and piece of content is a node in the tree. 

- The DOM allows JavaScript and other programming languages to interact with the web page, access its elements, modify its content, and respond to user interactions.

- When a web page is loaded in a browser, the browser parses the HTML or XML code and creates a representation of the document in memory, known as the DOM tree. This tree-like structure is then made accessible to scripts running on the page.

- The role of the DOM in web development is to provide a standardized and platform-independent way to access and modify the content and structure of web documents. 

- It allows developers to dynamically manipulate the elements of a web page, change their properties, add or remove elements, and respond to user actions such as clicks or form submissions.

- Developers can traverse the DOM tree, select specific elements based on their IDs, classes, or other attributes, and modify their content, styles, or attributes.
# Understanding hierarchical structure of the DOM
 
- The topmost node in the DOM tree is the "document" node, which represents the entire HTML or XML document. The document node has child nodes, which typically include the "head" and "body" nodes.

- The "head" node contains meta-information about the document, such as the document title, linked stylesheets, scripts, and other metadata. 

- The "body" node represents the main content of the document and contains child nodes representing elements like headings, paragraphs, images, links, and so on.

- Within the "body" node, there can be multiple levels of nesting. For example, you may have a "div" element that contains several "p" (paragraph) elements, and each "p" element may contain further nested elements like "strong" (bold text) or "a" (anchor/link) elements.

- Each element in the DOM can have attributes, such as "id" or "class," which provide additional information or help identify the elements for styling or scripting purposes.

- When you interact with the DOM using JavaScript or other programming languages, you can access and manipulate the elements by traversing the tree structure.


# Accessing DOM Elements

### Selecting Elements 

When working with the Document Object Model (DOM) in JavaScript, there are various methods available to select and manipulate elements based on different criteria. Here are some common methods for selecting elements:

1. `getElementById`: This method allows you to select an element based on its unique "id" attribute. It returns the element as a single object. For example: 
```js
var element = document.getElementById("myElementId");
```
2. `getElementsByClassName`: This method selects elements based on their class name. It returns a collection of elements as an HTMLCollection or a NodeList. You can access individual elements by their index. For example: 
```js
var elements = document.getElementsByClassName("myClass");
```
3. `getElementsByTagName`: This method selects elements based on their tag name. It returns a collection of elements with the specified tag name. Similarly, you can access individual elements by their index. For example: 
```js
var elements = document.getElementsByTagName("p");
```
4. `querySelector`: This method allows you to select elements using CSS-style selectors. It returns the first matching element found in the document. For example: 
```js
var element = document.querySelector("#myElementId");
```
5. `querySelectorAll`: This method is similar to querySelector but returns a collection of all matching elements. It returns a NodeList that you can iterate over. For example: 
```js
var elements = document.querySelectorAll(".myClass");
```
6. `parentNode` and `childNodes`: These properties allow you to navigate through the DOM hierarchy. parentNode gives you the direct parent of an element, while childNodes gives you a collection of all child nodes (including elements, text nodes, etc.). For example: 
```js
var parent = element.parentNode;
var children = parent.childNodes;
```
7.`Traversing through the DOM`: You can also traverse the DOM using properties like nextSibling, previousSibling, firstChild, and lastChild to move between sibling and child nodes. For example: 
```js
var nextSibling = element.nextSibling;
var firstChild = parent.firstChild;
```
### Accessing parent, child, and sibling elements
```js
<div id="parent">
  <h1>Parent Element</h1>
  <div id="child">
    <h2>Child Element</h2>
  </div>
  <div id="sibling">
    <h2>Sibling Element</h2>
  </div>
</div>
```
To access these elements using JavaScript, you can utilize methods like `getElementById`, `querySelector`, and properties like `parentNode`, `children`, and `nextSibling`.

1. **Accessing the parent element**: To access the parent element of a given element, you can use the `parentNode` property.
```js
const childElement = document.getElementById('child');
const parentElement = childElement.parentNode;
console.log(parentElement); // Output: <div id="parent">...</div>
```

2.**Accessing child elements**: To access child elements of a parent element, you can use the `children` property or the `querySelector` method. Here are examples using both approaches:
```js
const parentElement = document.getElementById('parent');
   const childElements = parentElement.children;
   console.log(childElements); // Output: HTMLCollection [ <h1>...</h1>, <div id="child">...</div>, <div id="sibling">...</div> ]
```
3. **Accessing sibling elements**: To access sibling elements of a given element, you can use the `nextSibling` and `previousSibling` property.
```js
var element = document.getElementById('yourElementId');
var nextSibling = element.nextSibling;
var previousSibling = element.previousSibling;
```
The nextElementSibling property returns the next sibling element node (skipping text nodes), while previousElementSibling returns the previous sibling element node. 
```js
var element = document.getElementById('yourElementId');
var nextSibling = element.nextElementSibling;
var previousSibling = element.previousElementSibling;
```
# Modifying Element Content and Attributes

### Changing text content of elements
 
1. **innerText**:
 It is a property that represents the visible text content of an element, excluding any child elements or HTML tags. It returns only the text content, ignoring any styling or formatting applied to the element. 
```js
<div id="myDiv">
  This is some <strong>bold</strong> text.
</div>

const div = document.getElementById('myDiv');
const innerText = div.innerText;
console.log(innerText);
```
2. **innerHTML**:
- It is similar to innerText, but it returns the complete HTML content, including any child elements or HTML tags within the element. It represents the content as a string of HTML.

- Note that when using `innerHTML`, you need to be cautious about security risks such as cross-site scripting (XSS) attacks, as it allows you to modify the HTML content of an element directly.
```js
const div = document.getElementById('myDiv');
const innerHTML = div.innerHTML;
console.log(innerHTML);
```
3. **textContent**:
It is another property that returns the text content of an element, similar to `innerText`. However, unlike `innerText`, it includes all the text content, even if it's hidden with CSS or contained within child elements.
```js
const div = document.getElementById('myDiv');
const textContent = div.textContent;
console.log(textContent);
```
### Modifying HTML attributes
 
1. Modifying the `class` attribute
```js
<div id="myDiv" class="old-class">Hello, World!</div>

const div = document.getElementById('myDiv');
div.className = 'new-class';

<div id="myDiv" class="new-class">Hello, World!</div> //Output
```
2. `setAttribute` method
```js
const div = document.getElementById('myDiv');
div.setAttribute('class', 'new-class');
```

3. Modifying the `src` attribute of an `<img>` tag
```js
<img id="myImage" src="old-image.jpg" alt="Old Image"/>

const image = document.getElementById('myImage');
image.src = 'new-image.jpg';

<img id="myImage" src="new-image.jpg" alt="Old Image"/> //output
``` 
4. Modifying the `href` attribute of an `<a>` tag
```js
<a id="myLink" href="old-url">Old Link</a>

const link = document.getElementById('myLink');
link.href = 'new-url';

<a id="myLink" href="new-url">Old Link</a>
```
# Adding, removing, and modifying CSS classes
```js
// 1.Adding
const element = document.getElementById('myElement');
element.classList.add('new-class');
// 2.Remove
const element = document.getElementById('myElement');
element.classList.remove('old-class');
// 3.Modify
const element = document.getElementById('myElement');
element.classList.remove('old-class');
element.classList.add('new-class');
//or
const element = document.getElementById('myElement');
element.classList.toggle('active');
```
# Creating new elements dynamically
  
1. **Create the new element**: 
Use the `createElement` method to create a new element of the desired type. Specify the HTML tag name for the element you want to create.
```js
const newElement = document.createElement('div');
```
2. **Set properties and attributes**: 
If you want to set properties or attributes for the newly created element, you can do so using JavaScript. For example, you can set the `id`, `class`, or other attributes.
```js
newElement.id = 'myNewElement';
newElement.className = 'new-class';
newElement.setAttribute('data-custom', 'value');
```
3. **text content or HTML**:
If you want to add text or HTML content inside the new element, you can use the `textContent` or `innerHTML` properties.
```js
newElement.textContent = 'This is the new element';
// or
newElement.innerHTML = '<strong>This is the new element</strong>';
```

# Appending, inserting, and removing elements from the DOM
 
1. `appendChild()`:
It adds the element at the end of the child nodes of the target element.
```js
const parentElement = document.getElementById('parent');
const newElement = document.createElement('div');
parentElement.appendChild(newElement);
```
2. `insertBefore()` - Inserts an element before a specified sibling element.
```js
var parentElement = document.getElementById('parentElementId');
var existingElement = document.getElementById('existingElementId');
var newElement = document.createElement('div');
parentElement.insertBefore(newElement, existingElement);
```
3. `insertAdjacentElement()` - Inserts an element at a specified position relative to another element.
```js
var targetElement = document.getElementById('targetElementId');
var newElement = document.createElement('div');

// 'beforebegin': Inserts newElement as a previous sibling of targetElement
targetElement.insertAdjacentElement('beforebegin', newElement);
// 'afterbegin': Inserts newElement as the first child of targetElement
targetElement.insertAdjacentElement('afterbegin', newElement);
// 'beforeend': Inserts newElement as the last child of targetElement
targetElement.insertAdjacentElement('beforeend', newElement);
// 'afterend': Inserts newElement as a following sibling of targetElement
targetElement.insertAdjacentElement('afterend', newElement);
```
4. `prepend() `- Adds an element as the first child of another element.
```js
var parentElement = document.getElementById('parentElementId');
var newElement = document.createElement('div');
parentElement.prepend(newElement);
```
5. `after()` - Inserts an element after another element.
```js
var existingElement = document.getElementById('existingElementId');
var newElement = document.createElement('div');
existingElement.after(newElement);
```
6. `before()` - Inserts an element before another element.

```js
var existingElement = document.getElementById('existingElementId');
var newElement = document.createElement('div');
existingElement.before(newElement);
```
7. **Removing an element**:
To remove an element from the DOM, you can use the `removeChild` method or the `remove` method (available in modern browsers). Both methods remove the element from its parent.
```js
const parentElement = document.getElementById('parent');
const elementToRemove = document.getElementById('toBeRemoved');
parentElement.removeChild(elementToRemove);
//or
const elementToRemove = document.getElementById('toBeRemoved');
elementToRemove.remove();
```
# Traversing the DOM

Navigating the DOM (Document Object Model) tree using parent, child, and sibling relationships in JavaScript allows you to access and manipulate elements based on their hierarchical position within the DOM. Here's how you can navigate the DOM tree using these relationships:
### Accessing parent elements 

To access the parent element of a specific element, you can use the `parentNode` property. It returns the immediate parent node of the current element.
```js
const element = document.getElementById('myElement');
const parentElement = element.parentNode;
```
### Accessing child elements 
```js
<div id="myElement">
  Text Node
  <p>Child Element 1</p>
  <span>Child Element 2</span>
  <!-- Comment Node -->
  <p>Child Element 3</p>
</div>

const element = document.getElementById('myElement');

const childNodes = element.childNodes;
console.log(childNodes);
/*  
Ouput of childNodes:
*/
NodeList(7) [text, p, span, comment, p, text, div#myElement]
```
  
The `childNodes` collection includes all types of nodes within the `myElement` div. It includes the following nodes:
1. Text Node: Represents the text content "Text Node".
2. Paragraph Element Node: `<p>Child Element 1</p>`.
3. Span Element Node: `<span>Child Element 2</span>`.
4. Comment Node: Represents the comment `<!-- Comment Node -->`.
5. Paragraph Element Node: `<p>Child Element 3</p>`.
6. Text Node: Represents the whitespace between the last paragraph and the closing `</div>` tag.
7. Div Element Node: `<div id="myElement">...</div>` itself.
```js
const children = element.children;
console.log(children);
// Output of children:
HTMLCollection(3) [p, span, p]
```
 
The `children` collection includes only the direct child element nodes within the `myElement` div. It excludes text nodes and non-element nodes. In this case, it includes the following elements:
1. Paragraph Element: `<p>Child Element 1</p>`.
2. Span Element: `<span>Child Element 2</span>`.
3. Paragraph Element: `<p>Child Element 3</p>`.

As you can see, the `children` collection only contains the direct child elements and excludes the text nodes and comment node.
### Accessing sibling elements
 
To access sibling elements of a specific element, you can use properties like `previousSibling`, `nextSibling`, `previousElementSibling`, and `nextElementSibling`. The `previousSibling` property returns the previous sibling node (including text nodes), `nextSibling` returns the next sibling node (including text nodes), `previousElementSibling` returns the previous sibling element node, and `nextElementSibling` returns the next sibling element node.
```js
const element = document.getElementById('myElement');
const previousSibling = element.previousSibling;
const nextSibling = element.nextSibling;
const previousElementSibling = element.previousElementSibling;
const nextElementSibling = element.nextElementSibling;
```
