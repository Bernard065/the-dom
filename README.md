# the-dom

Document Object Model(DOM)
Mastering the DOM: A Comprehensive Guide to Dynamic Web Development
bernard bebeni
bernard bebeni

4 min read
·
Just now






What is the DOM
The Document Object Model(DOM) is a programming interface for web documents. It represents the structure of an HTML document as a tree of objects. The DOM helps developers to access and manipulate the content, structure and style of webpages.

Let’s dive into the DOM in detail.

Example of HTML DOM
<!DOCTYPE html>
<html>
<head>
  <title>DOM Example</title>
</head>
<body>
  <h1 id="main-heading">Hello, DOM!</h1>
  <p class="text">This is a paragraph.</p>
  <ul>
    <li>First item</li>
    <li>Second item</li>
  </ul>
</body>
</html>
The DOM tree structure for the above code looks like:

Document
 └── html
      ├── head
      ├── title
      └── body
            ├── h1
            ├── p
            └── ul
                 ├── li
                 └── li
Key DOM Concepts
1. Selecting Elements:
To manipulate or access elements, you need to select them.

Methods:

getElementById()
getElementsByClassName()
getElementsByTagName()
querySelector()
querySelectorAll()
Example

const heading = document.querySelector("#main-heading");
const items = document.querySelectorAll("li");
console.log(items[1].innerText); // Outputs: "Second item
2. Traversing the DOM
DOM traversal allows you to navigate the tree structure.

Methods:

a. Parent nodes:

parentNode, parentElement
b. Child nodes:

childNodes, children, firstChild, lastChild
c. Sibling nodes:

nextSibling, previousSibling
Example

const ul = document.querySelector("ul");
console.log(ul.children[0].innerText); // Outputs: "First item
3. Manipulating the DOM
You can dynamically add, remove or modfy elements.

a. Changing Content
You can modify the content of an HTML element using properties such as innerHTML, innerText, and textContent.

i. innerHTML: Represents the HTML content inside an element, including tags. It can be used to read or set content.

NOTE: Settng innerHTML with untrusted content can expose your site to Cross-Site Scripting(XSS) attacks.

Example:

<div id="content">Hello, World!</div>
// Get the content
const div = document.getElementById("content");
console.log(div.innerHTML); // Output: "Hello, World!

// Set new HTML content
div.innerHTML = "<p>Welcome to the DOM!</p>";
ii. innerText: Represents the visible text inside an element. It ignores hidden text (e.g., text styled with display: none or visibility: hidden).

Example

<div id="content">
  <p>Hello, <span style="display: none;">invisible</span> World!</p>
</div>
const div = document.getElementById("content");
console.log(div.innerText); // Output: "Hello, World!
iii. textContent: Returns the text content of an element and all its descendants. It includes hidden text but does not process HTML tags.

<div id="content">
  <p>Hello, <span style="display: none;">invisible</span> World!</p>
</div>
const div = document.getElementById("content");
console.log(div.textContent); // Output: "Hello, invisible World!
b. Adding Elements
Adding elements means creating new HTML elements and placing them into the DOM.

i. createElement(): Creates a new element but does not add it to the page immediately.

Example:

const newDiv = document.createElement("div");
newDiv.innerText = "This is a new div.";
At this stage, newDiv exists in memory but is not visible on the webpage yet.

ii. appendChild(): Adds an element as the last child of a parent element.

Example:

<ul id="list"></ul>
const ul = document.getElementById("list");
const li = document.createElement("li");
li.innerText = "New List Item";
// Add the <li> to the <ul>
ul.appendChild(li);
Results:

<ul id="list">
  <li>New List Item</li>
</ul>
iii. append(): Adds multiple elements or text at once as the last child.

Example:

<ul id="list"></ul>
const ul = document.getElementById("list");
const li1 = document.createElement("li");
li1.innerText = "Item 1";

const li2 = document.createElement("li");
li2.innerText = "Item 2";

// Add both <li> elements at once
ul.append(li1, li2);
Results:

<ul id="list">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
c. Removing Elements:
Allows you to dynamically delete parts of your webpage.

i. removeChild(): Removes a specific child element from its parent.

<ul id="list">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
const ul = document.getElementById("list");
const firstItem = ul.children[0]; // Select the first <li>
ul.removeChild(firstItem); // Remove it
Results:

<ul id="list">
  <li>Item 2</li>
</ul>
ii. remove(): Directly removes an element from the DOM.

Example:

<p id="paragraph">This is a paragraph.</p>
const paragraph = document.getElementById("paragraph");
paragraph.remove(); // Remove the <p> element
Result: The paragraph is no longer part of the webpage.

d. Styling with the DOM
You can manipulate the CSS of elements using JavaScript.

Inline Styles:

style property
Example:

const heading = document.getElementById("main-heading");
heading.style.color = "blue";
heading.style.fontSize = "24px";
Classes:

classList provides methods like add(), remove(), toggle()
Example:

const para = document.querySelector(".text");
para.classList.add("highlight");
e. Handling Events
Events allow you to make the webpage interactive.

Common Events:

click, mouseover, mouseout, keydown, submit
Adding Event Listeners:

document.querySelector("button").addEventListener("click", () => {
  alert("Button clicked!");
});
Advanced DOM Concepts
a. Event Delegation

Instead of adding events to multiple child elements, delegate to a parent.

Example:

document.querySelector("ul").addEventListener("click", (event) => {
  if (event.target.tagName === "LI") {
    console.log(event.target.innerText);
  }
});
Conclusion
The DOM is key to interactive web development. It lets developers interact with and manipulate web pages dynamically. By mastering concepts like traversing, modifying elements, handling events, and managing styles, you can create engaging user interfaces. With practice, you can build functional and delightful applications. Understanding the DOM is essential for becoming a skilled web developer.