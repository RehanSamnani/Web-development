# JavaScript Detailed Notes

## 1. Introduction & Syntax
JavaScript is a versatile, high-level programming language primarily used for web development. It is case-sensitive and uses curly braces `{}` for code blocks. Statements usually end with a semicolon `;`.

```js
// This is a single-line comment
/* This is a 
   multi-line comment */
console.log("Hello, World!");
```

## 2. Variables & Data Types
Variables store data. Use `let` and `const` (block-scoped, ES6+) or `var` (function-scoped, legacy).

- `let`: Can be updated, not redeclared in the same scope.
- `const`: Cannot be updated or redeclared. Must be initialized.
- `var`: Can be updated and redeclared, function-scoped.

Data types:
- String, Number, Boolean, Null, Undefined, Object, Symbol, BigInt

```js
let name = "Alice"; // String
const age = 30;     // Number
let isStudent = true; // Boolean
let nothing = null;   // Null
let notDefined;       // Undefined
let person = { name: "Bob" }; // Object
let big = 123n;      // BigInt
```

## 3. Operators
- Arithmetic: `+`, `-`, `*`, `/`, `%`, `**`
- Assignment: `=`, `+=`, `-=`, `*=`, `/=`, `%=`
- Comparison: `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`
- Logical: `&&`, `||`, `!`
- Ternary: `condition ? expr1 : expr2`

```js
let sum = 5 + 3; // 8
let isEqual = (5 == '5'); // true (loose equality)
let isStrictEqual = (5 === '5'); // false (strict equality)
let result = (age >= 18) ? "Adult" : "Minor";
```

## 4. Control Flow
### If-Else
Executes code blocks based on conditions.
```js
if (score > 90) {
  console.log("Excellent");
} else if (score > 75) {
  console.log("Good");
} else {
  console.log("Needs Improvement");
}
```
### Switch
Selects code to run based on a variable's value.
```js
let day = 2;
switch(day) {
  case 1:
    console.log("Monday");
    break;
  case 2:
    console.log("Tuesday");
    break;
  default:
    console.log("Other day");
}
```
### Loops
Repeat code multiple times.
```js
for (let i = 0; i < 3; i++) {
  console.log(i);
}

let j = 0;
while (j < 3) {
  console.log(j);
  j++;
}

do {
  console.log(j);
  j--;
} while (j > 0);
```

## 5. Functions
Functions are reusable blocks of code. They can take parameters and return values.

- Function Declaration:
```js
function greet(name) {
  return "Hello, " + name + "!";
}
console.log(greet("Alice"));
```
- Function Expression:
```js
const add = function(a, b) {
  return a + b;
};
console.log(add(2, 3));
```
- Arrow Function (ES6+):
```js
const multiply = (a, b) => a * b;
console.log(multiply(4, 5));
```

## 6. Objects
Objects store related data and functions (methods) as key-value pairs.
```js
const car = {
  brand: "Toyota",
  model: "Corolla",
  year: 2020,
  start: function() {
    console.log("Car started");
  }
};
console.log(car.brand); // Toyota
car.start();
car.year = 2021; // Modify property
```

## 7. Arrays
Arrays are ordered lists of values, indexed from 0.
```js
let fruits = ["Apple", "Banana", "Cherry"];
console.log(fruits[1]); // Banana
fruits.push("Date"); // Add
fruits.pop(); // Remove last
fruits.forEach(fruit => console.log(fruit));
```

## 8. String, Number, Math, Date
- String methods: `length`, `toUpperCase()`, `slice()`, `split()`, `replace()`
- Number methods: `parseInt()`, `parseFloat()`, `toFixed()`
- Math: `Math.random()`, `Math.floor()`, `Math.max()`
- Date: `new Date()`, `getFullYear()`, `getMonth()`

```js
let text = "Hello World";
console.log(text.toUpperCase()); // "HELLO WORLD"
let num = 3.14159;
console.log(num.toFixed(2)); // "3.14"
console.log(Math.floor(Math.random() * 10)); // Random 0-9
let now = new Date();
console.log(now.getFullYear());
```

## 9. Scope & Hoisting
- Scope: Where variables are accessible (global, function, block).
- Hoisting: Declarations are moved to the top of their scope.

```js
function test() {
  console.log(a); // undefined (hoisted)
  var a = 5;
}
test();
```

## 10. Closures
A closure is a function that remembers variables from its outer scope.
```js
function makeCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

## 11. ES6+ Features
- Template literals: ``Hello, ${name}``
- Destructuring:
```js
let [a, b] = [1, 2];
let {x, y} = {x: 10, y: 20};
```
- Spread/Rest:
```js
let arr1 = [1, 2];
let arr2 = [...arr1, 3]; // [1,2,3]
function sum(...nums) { return nums.reduce((a, b) => a + b); }
```
- Classes:
```js
class Animal {
  constructor(name) { this.name = name; }
  speak() { console.log(this.name + " makes a noise."); }
}
let dog = new Animal("Rex");
dog.speak();
```
- Modules:
```js
// In module1.js
export const pi = 3.14;
// In module2.js
import { pi } from './module1.js';
```

## 12. DOM Manipulation
Interact with web page elements.
```js
document.getElementById("demo").textContent = "Hello!";
let el = document.querySelector(".my-class");
el.style.color = "red";
el.classList.add("active");
```

## 13. Events
Respond to user actions.
```js
let btn = document.getElementById("myBtn");
btn.addEventListener("click", function(event) {
  alert("Button clicked!");
  event.preventDefault();
});
```

## 14. Error Handling
Handle errors gracefully.
```js
try {
  throw new Error("Something went wrong");
} catch (e) {
  console.log(e.message);
} finally {
  console.log("Always runs");
}
```

## 15. JSON
JavaScript Object Notation for data exchange.
```js
let obj = { name: "Alice" };
let jsonStr = JSON.stringify(obj);
let parsed = JSON.parse(jsonStr);
```

## 16. Promises & Async/Await
Handle asynchronous operations.
```js
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Done!"), 1000);
});
promise.then(result => console.log(result));

async function getData() {
  let res = await fetch("https://api.example.com");
  let data = await res.json();
  return data;
}
```

## 17. Useful Built-in Methods
- Array: `map()`, `filter()`, `reduce()`, `find()`, `includes()`
```js
let nums = [1,2,3,4];
let squares = nums.map(x => x*x); // [1,4,9,16]
let even = nums.filter(x => x%2===0); // [2,4]
let sum = nums.reduce((a,b) => a+b, 0); // 10
```
- String: `includes()`, `startsWith()`, `endsWith()`
```js
let str = "JavaScript";
console.log(str.includes("Script")); // true
```
- Object: `Object.keys()`, `Object.values()`, `Object.entries()`
```js
let obj = {a:1, b:2};
console.log(Object.keys(obj)); // ["a","b"]
```

---
This expanded guide covers all major JavaScript topics with detailed explanations and examples. For more, refer to the official documentation or request advanced topics!