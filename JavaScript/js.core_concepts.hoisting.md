> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Hoisting

#javascript #programming #javascript #core-concepts #hoisting

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Hoisting

## Definition

Hoisting is JavaScript's behavior of moving variable and function declarations to the top of their scope during compilation, before code execution.

## Variable Hoisting

### var Hoisting

```js
console.log(x); // undefined (not an error!)
var x = 5;
console.log(x); // 5

// JavaScript interprets this as:
var x; // Declaration hoisted
console.log(x); // undefined
x = 5; // Assignment stays in place
console.log(x); // 5
```

### let and const - Temporal Dead Zone

```js
console.log(x); // ReferenceError: Cannot access 'x' before initialization
let x = 5;

console.log(y); // ReferenceError
const y = 10;
```

The "Temporal Dead Zone" (TDZ) is the area from the start of the block until the declaration.

```js
{
  // TDZ starts
  console.log(x); // ReferenceError
  // TDZ ends
  let x = 5;
  console.log(x); // 5
}
```

## Function Hoisting

### Function Declarations

Function declarations are fully hoisted (both declaration AND body).

```js
greet(); // "Hello!" - works!

function greet() {
  console.log("Hello!");
}
```

### Function Expressions

Only the variable declaration is hoisted, not the function.

```js
greet(); // TypeError: greet is not a function

var greet = function () {
  console.log("Hello!");
};
```

```js
// JavaScript sees it as:
var greet;         // Declaration hoisted
greet();           // greet is undefined, can't call it
greet = function() { ... };  // Assignment stays
```

### Arrow Functions

Same as function expressions - not hoisted.

```js
greet(); // TypeError or ReferenceError

const greet = () => console.log("Hello!");
```

## Comparison Table

| Declaration          | Hoisted       | Initialized | TDZ     |
| -------------------- | ------------- | ----------- | ------- |
| `var`                | Yes           | `undefined` | No      |
| `let`                | Yes           | No          | Yes     |
| `const`              | Yes           | No          | Yes     |
| Function Declaration | Yes           | Yes (full)  | No      |
| Function Expression  | Variable only | No          | Depends |
| Class                | Yes           | No          | Yes     |

## Class Hoisting

Classes are hoisted but not initialized (TDZ applies).

```js
const p = new Person(); // ReferenceError

class Person {
  constructor() {}
}
```

## Hoisting in Practice

### Why Understanding Hoisting Matters

```js
// This works
function outer() {
  inner(); // Works because inner is hoisted

  function inner() {
    console.log("Inner called");
  }
}

// This doesn't
function outer() {
  inner(); // TypeError

  var inner = function () {
    console.log("Inner called");
  };
}
```

### Common Pitfall

```js
var name = "Global";

function showName() {
  console.log(name); // undefined, not "Global"!
  var name = "Local";
  console.log(name); // "Local"
}

// Because JavaScript sees:
function showName() {
  var name; // Hoisted to top of function
  console.log(name); // undefined
  name = "Local";
  console.log(name); // "Local"
}
```

## Best Practices

### Always Declare at the Top

```js
// Good
function calculate() {
  let result;
  let multiplier = 2;

  // ... rest of function
}
```

### Use let and const

```js
// Avoid
var x = 5;

// Prefer - prevents hoisting confusion
let x = 5;
const y = 10;
```

### Initialize When Declaring

```js
// Avoid
let count;
// ... many lines later
count = 0;

// Prefer
let count = 0;
```

## Key Points

> var declarations are hoisted and initialized to undefined

> let and const are hoisted but not initialized (TDZ)

> Function declarations are fully hoisted

> Function expressions are NOT hoisted

> Use let/const to avoid hoisting-related bugs

## Links

- [MDN Hoisting](https://developer.mozilla.org/en-US/docs/Glossary/Hoisting)
