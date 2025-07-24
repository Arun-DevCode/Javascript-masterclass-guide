JavaScript Learning Guide
This comprehensive guide is designed for learners from beginner to advanced levels, covering essential JavaScript concepts. Each section includes explanations, code examples at different skill levels (beginner, intermediate, advanced), and real-time exercises to reinforce learning. The guide is structured to help you progressively build your JavaScript skills and apply them in practical scenarios.
Table of Contents

JavaScript Introduction & Basics
Data Types - Primitive & Reference
Operators & Expressions
Control Statements - Conditional & Looping
Assignment: 6 Programs
Functions - Function, Parameters, Return Statement
Arrow Functions & Callbacks
JavaScript DOM & Selectors
Assignment: 7 DOM Programs
Events & Event Listeners
Form Submission & Validation
JavaScript on a Webpage
Assignment: To-Do List
APIs - Fetch API, then, catch, JSON, and Objects
Asynchronous JavaScript: Callback/Callback Hell/Promise/Async Await
JavaScript Program with API (Phonebook with Fetch API and Asynchronous JavaScript)
Arrays & Array Functions
Rest & Spread Operator, Map, Filter, Reduce, ForEach
Web Development Using JavaScript
Revising Advanced JavaScript


JavaScript Introduction & Basics
OverviewJavaScript is a versatile programming language used primarily for web development. Key concepts include variables (let, var, const), data types, and basic syntax.
Code Example  

Beginner: Declaring Variables

let name = "Alice"; // Reassignable
const age = 25; // Non-reassignable
var score = 90; // Older way, function-scoped
console.log(name, age, score);


Intermediate: Variable Scope

function testScope() {
  let x = 10;
  if (true) {
    let x = 20; // Block-scoped, doesn't affect outer x
    console.log("Inside block:", x); // 20
  }
  console.log("Outside block:", x); // 10
}
testScope();


Advanced: Closures with Variables

function createCounter() {
  let count = 0;
  return function () {
    return count++;
  };
}
const counter = createCounter();
console.log(counter()); // 0
console.log(counter()); // 1

ExerciseReal-Time Task: Create a simple calculator that uses let to store two numbers and const for a result. Allow users to input numbers via prompt() and display the sum, difference, product, and quotient.

Data Types - Primitive & Reference
OverviewJavaScript has primitive types (e.g., string, number, boolean) and reference types (e.g., objects, arrays). Primitives are immutable, while references are mutable.
Code Example  

Beginner: Checking Types

const str = "Hello";
const num = 42;
const obj = { name: "Bob" };
console.log(typeof str); // string
console.log(typeof num); // number
console.log(typeof obj); // object


Intermediate: Copying Primitives vs. References

let num1 = 10;
let num2 = num1; // Copy value
num2 = 20;
console.log(num1); // 10 (unchanged)

let arr1 = [1, 2, 3];
let arr2 = arr1; // Copy reference
arr2.push(4);
console.log(arr1); // [1, 2, 3, 4] (modified)


Advanced: Deep Copying Objects

const original = { a: 1, b: { c: 2 } };
const deepCopy = JSON.parse(JSON.stringify(original)); // Deep copy
deepCopy.b.c = 3;
console.log(original.b.c); // 2 (original unchanged)

ExerciseReal-Time Task: Create an object representing a student (name, age, grades array). Write a function to create a deep copy of the student object and modify the copy without affecting the original.

Operators & Expressions
OverviewOperators include arithmetic (+, -), comparison (==, ===), logical (&&, ||), and more. Expressions combine operators and values.
Code Example  

Beginner: Basic Arithmetic

const a = 10;
const b = 5;
console.log(a + b); // 15
console.log(a > b); // true
console.log(a === b); // false


Intermediate: Ternary Operator

const age = 20;
const status = age >= 18 ? "Adult" : "Minor";
console.log(status); // Adult


Advanced: Short-Circuit Evaluation

function getUser() {
  return null;
}
const user = getUser() || { name: "Guest", role: "user" };
console.log(user.name); // Guest (fallback due to null)

ExerciseReal-Time Task: Write a function that takes two numbers and an operator (+, -, *, /) as input and returns the result using a switch statement. Handle invalid operators with a default case.

Control Statements - Conditional & Looping
OverviewConditional statements (if, switch) control flow based on conditions. Looping statements (for, while, do-while) handle repetition.
Code Example  

Beginner: If-Else

const score = 85;
if (score >= 90) {
  console.log("A");
} else if (score >= 80) {
  console.log("B");
} else {
  console.log("C");
}


Intermediate: For Loop

for (let i = 1; i <= 5; i++) {
  console.log(`Number ${i}`);
}


Advanced: Nested Loops with Break

for (let i = 1; i <= 3; i++) {
  for (let j = 1; j <= 3; j++) {
    if (i === 2 && j === 2) break; // Breaks inner loop
    console.log(`i=${i}, j=${j}`);
  }
}

ExerciseReal-Time Task: Write a program to print a multiplication table (1 to 10) using nested loops. Allow the user to input a number to display only that table.

Assignment: 6 Programs
OverviewPractice the basics with these programs:

Swap two variables using a temporary variable.
Check if a number is even or odd.
Calculate the factorial of a number.
Reverse a string.
Find the largest number in an array.
Check if a string is a palindrome.

Example: Palindrome Check  
function isPalindrome(str) {
  str = str.toLowerCase().replace(/[^a-z0-9]/g, "");
  return str === str.split("").reverse().join("");
}
console.log(isPalindrome("A man, a plan, a canal: Panama")); // true

ExerciseReal-Time Task: Write a program to check if a user-input string is a palindrome and display the result in the console.

Functions - Function, Parameters, Return Statement
OverviewFunctions are reusable blocks of code that can take parameters and return values.
Code Example  

Beginner: Basic Function

function greet(name) {
  return `Hello, ${name}!`;
}
console.log(greet("Alice")); // Hello, Alice!


Intermediate: Default Parameters

function calculateArea(length = 1, width = 1) {
  return length * width;
}
console.log(calculateArea(5)); // 5 (width defaults to 1)


Advanced: Higher-Order Function

function createMultiplier(factor) {
  return function (num) {
    return num * factor;
  };
}
const double = createMultiplier(2);
console.log(double(5)); // 10

ExerciseReal-Time Task: Create a function that calculates the total price of items in a cart, applying a discount percentage passed as a parameter.

Arrow Functions & Callbacks
OverviewArrow functions provide a concise syntax. Callbacks are functions passed as arguments to other functions.
Code Example  

Beginner: Arrow Function

const add = (a, b) => a + b;
console.log(add(2, 3)); // 5


Intermediate: Callback Example

function processData(data, callback) {
  const result = data.toUpperCase();
  callback(result);
}
processData("hello", (res) => console.log(res)); // HELLO


Advanced: Callback with Array

function filterArray(arr, callback) {
  const result = [];
  for (let item of arr) {
    if (callback(item)) result.push(item);
  }
  return result;
}
const numbers = [1, 2, 3, 4];
console.log(filterArray(numbers, (n) => n % 2 === 0)); // [2, 4]

ExerciseReal-Time Task: Write a function that takes an array of numbers and a callback to filter out prime numbers, returning only primes.

JavaScript DOM & Selectors
OverviewThe Document Object Model (DOM) allows JavaScript to interact with HTML elements using selectors like getElementById, querySelector, etc.
Code Example  

Beginner: Selecting by ID

<div id="myDiv">Hello</div>
<script>
  const div = document.getElementById("myDiv");
  div.textContent = "World";
</script>


Intermediate: Query Selector

<div class="box">Box 1</div>
<div class="box">Box 2</div>
<script>
  const boxes = document.querySelectorAll(".box");
  boxes.forEach((box) => (box.style.backgroundColor = "lightblue"));
</script>


Advanced: Dynamic Element Creation

<div id="container"></div>
<script>
  const container = document.getElementById("container");
  const newDiv = document.createElement("div");
  newDiv.textContent = "Dynamic Div";
  newDiv.className = "box";
  container.appendChild(newDiv);
</script>

ExerciseReal-Time Task: Create a button that, when clicked, adds a new paragraph element with user-input text to a container div.

Assignment: 7 DOM Programs
OverviewPractice DOM manipulation with these programs:

Change text color on button click.
Toggle visibility of an element.
Create a dynamic list from user input.
Validate a form field (e.g., email format).
Update a counter display on button clicks.
Change background color based on user selection.
Display current time in a div, updating every second.

Example: Toggle Visibility  
<button onclick="toggle()">Toggle</button>
<div id="myDiv">Content</div>
<script>
  function toggle() {
    const div = document.getElementById("myDiv");
    div.style.display = div.style.display === "none" ? "block" : "none";
  }
</script>

ExerciseReal-Time Task: Create a button that toggles the visibility of an image on the page.

Events & Event Listeners
OverviewEvents (e.g., click, mouseover) trigger actions. addEventListener attaches handlers to elements.
Code Example  

Beginner: Click Event

<button id="btn">Click Me</button>
<script>
  document.getElementById("btn").addEventListener("click", () => {
    alert("Button clicked!");
  });
</script>


Intermediate: Multiple Events

<div id="box" style="width:100px;height:100px;background:lightblue"></div>
<script>
  const box = document.getElementById("box");
  box.addEventListener("mouseover", () => (box.style.backgroundColor = "lightgreen"));
  box.addEventListener("mouseout", () => (box.style.backgroundColor = "lightblue"));
</script>


Advanced: Event Delegation

<ul id="list">
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
<script>
  document.getElementById("list").addEventListener("click", (e) => {
    if (e.target.tagName === "LI") {
      e.target.style.color = "red";
    }
  });
</script>

ExerciseReal-Time Task: Create a list where clicking any item changes its text to "Clicked!" using event delegation.

Form Submission & Validation
OverviewForms collect user input. JavaScript validates input before submission.
Code Example  

Beginner: Basic Form

<form onsubmit="validate(event)">
  <input type="text" id="name" />
  <button type="submit">Submit</button>
</form>
<script>
  function validate(e) {
    e.preventDefault();
    const name = document.getElementById("name").value;
    if (name) alert(`Hello, ${name}!`);
    else alert("Name is required!");
  }
</script>


Intermediate: Email Validation

<form onsubmit="validateEmail(event)">
  <input type="email" id="email" />
  <button type="submit">Submit</button>
</form>
<script>
  function validateEmail(e) {
    e.preventDefault();
    const email = document.getElementById("email").value;
    const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    alert(regex.test(email) ? "Valid email" : "Invalid email");
  }
</script>


Advanced: Multiple Field Validation

<form onsubmit="validateForm(event)">
  <input type="text" id="name" />
  <input type="number" id="age" />
  <button type="submit">Submit</button>
</form>
<script>
  function validateForm(e) {
    e.preventDefault();
    const name = document.getElementById("name").value;
    const age = document.getElementById("age").value;
    if (!name || age < 18) {
      alert("Please fill all fields and ensure age is 18+");
    } else {
      alert("Form submitted!");
    }
  }
</script>

ExerciseReal-Time Task: Create a registration form with name, email, and password fields. Validate that the email is valid and the password is at least 8 characters long before submission.

JavaScript on a Webpage
OverviewJavaScript enhances webpages by adding interactivity, manipulating the DOM, and handling user actions.
Code Example  
<!DOCTYPE html>
<html>
<head>
  <title>Interactive Page</title>
</head>
<body>
  <button id="btn">Click Me</button>
  <div id="output"></div>
  <script>
    document.getElementById("btn").addEventListener("click", () => {
      document.getElementById("output").textContent = "Button clicked!";
    });
  </script>
</body>
</html>

ExerciseReal-Time Task: Create a webpage with a button that, when clicked, changes the background color of the page to a random color.

Assignment: To-Do List
OverviewBuild a to-do list application using DOM manipulation and event listeners.
Code Example  
<!DOCTYPE html>
<html>
<head>
  <title>To-Do List</title>
</head>
<body>
  <input type="text" id="taskInput" placeholder="Add a task" />
  <button onclick="addTask()">Add</button>
  <ul id="taskList"></ul>
  <script>
    function addTask() {
      const task = document.getElementById("taskInput").value;
      if (!task) return;
      const li = document.createElement("li");
      li.textContent = task;
      li.addEventListener("click", () => li.classList.toggle("completed"));
      document.getElementById("taskList").appendChild(li);
      document.getElementById("taskInput").value = "";
    }
  </script>
</body>
</html>

ExerciseReal-Time Task: Enhance the to-do list by adding a "Delete" button for each task that removes it when clicked.

APIs - Fetch API, then, catch, JSON, and Objects
OverviewThe Fetch API retrieves data from APIs. .then() and .catch() handle responses and errors. JSON is used to parse data.
Code Example  

Beginner: Basic Fetch

fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then((response) => response.json())
  .then((data) => console.log(data.title))
  .catch((error) => console.error("Error:", error));


Intermediate: Display API Data

<div id="output"></div>
<script>
  fetch("https://jsonplaceholder.typicode.com/users/1")
    .then((response) => response.json())
    .then((data) => {
      document.getElementById("output").textContent = data.name;
    })
    .catch((error) => console.error("Error:", error));
</script>


Advanced: Posting Data

fetch("https://jsonplaceholder.typicode.com/posts", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ title: "New Post", body: "Content", userId: 1 }),
})
  .then((response) => response.json())
  .then((data) => console.log("Posted:", data))
  .catch((error) => console.error("Error:", error));

ExerciseReal-Time Task: Fetch a list of users from jsonplaceholder.typicode.com/users and display their names in an HTML list.

Asynchronous JavaScript: Callback/Callback Hell/Promise/Async Await
OverviewAsynchronous JavaScript handles operations like API calls. Callbacks can lead to "callback hell." Promises and async/await simplify async code.
Code Example  

Beginner: Callback

function fetchData(callback) {
  setTimeout(() => callback("Data loaded"), 1000);
}
fetchData((data) => console.log(data));


Intermediate: Promise

function fetchDataPromise() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Data loaded"), 1000);
  });
}
fetchDataPromise().then((data) => console.log(data));


Advanced: Async/Await

async function fetchDataAsync() {
  const response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
  const data = await response.json();
  console.log(data.title);
}
fetchDataAsync().catch((error) => console.error("Error:", error));

ExerciseReal-Time Task: Write an async function to fetch and display a random quote from quotable.io/api/random.

JavaScript Program with API (Phonebook with Fetch API and Asynchronous JavaScript)
OverviewBuild a phonebook using an API to store and retrieve contacts.
Code Example  
<!DOCTYPE html>
<html>
<head>
  <title>Phonebook</title>
</head>
<body>
  <input type="text" id="name" placeholder="Name" />
  <input type="text" id="phone" placeholder="Phone" />
  <button onclick="addContact()">Add</button>
  <ul id="contactList"></ul>
  <script>
    async function addContact() {
      const name = document.getElementById("name").value;
      const phone = document.getElementById("phone").value;
      if (!name || !phone) return;
      await fetch("https://jsonplaceholder.typicode.com/users", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ name, phone }),
      });
      displayContacts();
    }
    async function displayContacts() {
      const response = await fetch("https://jsonplaceholder.typicode.com/users");
      const contacts = await response.json();
      const list = document.getElementById("contactList");
      list.innerHTML = "";
      contacts.forEach((contact) => {
        const li = document.createElement("li");
        li.textContent = `${contact.name}: ${contact.phone || "N/A"}`;
        list.appendChild(li);
      });
    }
    displayContacts();
  </script>
</body>
</html>

ExerciseReal-Time Task: Modify the phonebook to include a "Delete" button for each contact, removing it via a DELETE request to the API.

Arrays & Array Functions
OverviewArrays store lists of data. Methods like push, pop, map, filter, etc., manipulate arrays.
Code Example  

Beginner: Basic Array Methods

const arr = [1, 2, 3];
arr.push(4); // [1, 2, 3, 4]
arr.pop(); // [1, 2, 3]
console.log(arr);


Intermediate: Map and Filter

const numbers = [1, 2, 3, 4];
const doubled = numbers.map((n) => n * 2); // [2, 4, 6, 8]
const evens = numbers.filter((n) => n % 2 === 0); // [2, 4]
console.log(doubled, evens);


Advanced: Reduce

const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, curr) => acc + curr, 0); // 10
console.log(sum);

ExerciseReal-Time Task: Create an array of product objects (name, price). Use map to display names, filter to show products under $50, and reduce to calculate the total price.

Rest & Spread Operator, Map, Filter, Reduce, ForEach
OverviewThe spread (...) operator expands arrays/objects. Rest collects arguments into an array. Array methods enhance data processing.
Code Example  

Beginner: Spread Operator

const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4]; // [1, 2, 3, 4]
console.log(arr2);


Intermediate: Rest Parameters

function sum(...numbers) {
  return numbers.reduce((a, b) => a + b, 0);
}
console.log(sum(1, 2, 3, 4)); // 10


Advanced: Combining Methods

const items = [{ price: 10 }, { price: 20 }, { price: 30 }];
const total = items
  .filter((item) => item.price > 15)
  .map((item) => item.price)
  .reduce((a, b) => a + b, 0); // 50
console.log(total);

ExerciseReal-Time Task: Write a function that takes variable arguments using rest, filters out non-numbers, and returns their sum using reduce.

Web Development Using JavaScript
OverviewJavaScript powers interactive web applications, integrating DOM, events, and APIs.
Code Example  
<!DOCTYPE html>
<html>
<head>
  <title>Counter App</title>
</head>
<body>
  <button id="increment">Increment</button>
  <div id="count">0</div>
  <script>
    let count = 0;
    document.getElementById("increment").addEventListener("click", () => {
      count++;
      document.getElementById("count").textContent = count;
    });
  </script>
</body>
</html>

ExerciseReal-Time Task: Build a simple webpage with a button that fetches and displays a random dog image from dog.ceo/api/breeds/image/random.

Revising Advanced JavaScript
OverviewReview advanced concepts like closures, promises, async/await, and modern array methods.
Code Example  
async function fetchMultiple() {
  const [post, user] = await Promise.all([
    fetch("https://jsonplaceholder.typicode.com/posts/1").then((res) => res.json()),
    fetch("https://jsonplaceholder.typicode.com/users/1").then((res) => res.json()),
  ]);
  console.log(post.title, user.name);
}
fetchMultiple();

ExerciseReal-Time Task: Create a webpage that fetches and displays both a post title and user name from jsonplaceholder.typicode.com using Promise.all.

Getting Started
To use this guide:

Clone the repository: git clone <repository-url>
Open the relevant HTML or JavaScript files in a browser or code editor.
Complete the exercises to practice each concept.
Refer to the code examples for guidance on implementation.

Contributing
Contributions are welcome! Please submit a pull request with any improvements or additional exercises to enhance the learning experience.
License
This project is licensed under the MIT License - see the LICENSE file for details.