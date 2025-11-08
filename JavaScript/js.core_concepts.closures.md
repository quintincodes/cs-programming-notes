> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Closures

#javascript #programming #javascript #core-concepts #closures

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Closures

## Definition

A closure is a function that remembers and accesses variables from its outer scope, even after the outer function has finished executing.

## How Closures Work

```js
function outer() {
  const message = "Hello"; // Outer scope variable

  function inner() {
    console.log(message); // Accesses outer variable
  }

  return inner;
}

const greet = outer(); // outer() finishes
greet(); // 'Hello' - still has access to message!
```

## Simple Examples

### Counter

```js
function createCounter() {
  let count = 0; // Private variable

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
// count is private - can't access directly
```

### Factory Functions

```js
function createGreeter(greeting) {
  return function (name) {
    return `${greeting}, ${name}!`;
  };
}

const sayHello = createGreeter("Hello");
const sayHi = createGreeter("Hi");

console.log(sayHello("John")); // 'Hello, John!'
console.log(sayHi("Jane")); // 'Hi, Jane!'
```

## Common Use Cases

### Private Variables (Module Pattern)

```js
const bankAccount = (function () {
  let balance = 0; // Private

  return {
    deposit(amount) {
      balance += amount;
      return balance;
    },
    withdraw(amount) {
      if (amount <= balance) {
        balance -= amount;
        return balance;
      }
      return "Insufficient funds";
    },
    getBalance() {
      return balance;
    },
  };
})();

bankAccount.deposit(100); // 100
bankAccount.withdraw(30); // 70
bankAccount.balance; // undefined (private!)
```

### Event Handlers

```js
function setupButton(buttonId, message) {
  const button = document.getElementById(buttonId);

  button.addEventListener("click", function () {
    alert(message); // Closure - remembers message
  });
}

setupButton("btn1", "Button 1 clicked!");
setupButton("btn2", "Button 2 clicked!");
```

### Memoization

```js
function memoize(fn) {
  const cache = {}; // Closure - persists between calls

  return function (arg) {
    if (cache[arg]) {
      return cache[arg];
    }
    const result = fn(arg);
    cache[arg] = result;
    return result;
  };
}

const expensiveCalc = memoize(function (n) {
  console.log("Calculating...");
  return n * n;
});

expensiveCalc(5); // 'Calculating...' -> 25
expensiveCalc(5); // 25 (from cache, no log)
```

### Partial Application

```js
function multiply(a) {
  return function (b) {
    return a * b;
  };
}

const double = multiply(2);
const triple = multiply(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

## Common Pitfall: Loop Variables

```js
// Problem: All buttons alert '5'
for (var i = 0; i < 5; i++) {
  buttons[i].onclick = function () {
    alert(i); // i is shared, equals 5 after loop
  };
}

// Solution 1: Use let (block scope)
for (let i = 0; i < 5; i++) {
  buttons[i].onclick = function () {
    alert(i); // Each iteration has its own i
  };
}

// Solution 2: IIFE (creates new scope)
for (var i = 0; i < 5; i++) {
  (function (j) {
    buttons[j].onclick = function () {
      alert(j);
    };
  })(i);
}
```

## Closure vs Regular Function

```js
// Regular function - no closure
function add(a, b) {
  return a + b;
}

// Closure - remembers 'a'
function addWith(a) {
  return function (b) {
    return a + b; // 'a' is from outer scope
  };
}

const addWith5 = addWith(5);
addWith5(3); // 8
```

## Memory Considerations

```js
function heavyFunction() {
  const bigData = new Array(1000000).fill("data");

  return function () {
    // bigData is kept in memory as long as this function exists
    return bigData.length;
  };
}

const fn = heavyFunction();
// bigData stays in memory until fn is garbage collected
```

## Key Points

> Closures remember outer scope variables

> Used for private state and data encapsulation

> Factory functions use closures to customize behavior

> Be careful with memory - closed-over data persists

> Use let in loops to avoid closure pitfalls

## Links

- [MDN Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
