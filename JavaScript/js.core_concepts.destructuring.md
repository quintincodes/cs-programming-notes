> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Destructuring

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Destructuring

## Definition

Destructuring is a syntax that allows unpacking values from arrays or properties from objects into distinct variables.

## Array Destructuring

### Basic Syntax

```js
const colors = ["red", "green", "blue"];

// Old way
const first = colors[0];
const second = colors[1];

// Destructuring
const [first, second, third] = colors;
console.log(first); // 'red'
console.log(second); // 'green'
```

### Skipping Elements

```js
const numbers = [1, 2, 3, 4, 5];
const [first, , third] = numbers;
console.log(first); // 1
console.log(third); // 3
```

### Default Values

```js
const [a, b, c = "default"] = [1, 2];
console.log(c); // 'default'
```

### Rest Pattern

```js
const [head, ...tail] = [1, 2, 3, 4];
console.log(head); // 1
console.log(tail); // [2, 3, 4]
```

### Swapping Variables

```js
let a = 1,
  b = 2;
[a, b] = [b, a];
console.log(a); // 2
console.log(b); // 1
```

## Object Destructuring

### Basic Syntax

```js
const person = { name: "John", age: 30, city: "NYC" };

// Old way
const name = person.name;
const age = person.age;

// Destructuring
const { name, age, city } = person;
console.log(name); // 'John'
```

### Renaming Variables

```js
const { name: userName, age: userAge } = person;
console.log(userName); // 'John'
```

### Default Values

```js
const { name, country = "USA" } = person;
console.log(country); // 'USA'
```

### Nested Destructuring

```js
const user = {
  id: 1,
  info: {
    name: "John",
    address: { city: "NYC", zip: "10001" },
  },
};

const {
  info: {
    name,
    address: { city },
  },
} = user;
console.log(name); // 'John'
console.log(city); // 'NYC'
```

## Function Parameters

### Array Destructuring in Params

```js
function getFirst([first]) {
  return first;
}
getFirst([1, 2, 3]); // 1
```

### Object Destructuring in Params

```js
function greet({ name, age }) {
  console.log(`Hello ${name}, you are ${age}`);
}
greet({ name: "John", age: 30 });
```

### With Default Values

```js
function createUser({ name = "Guest", role = "user" } = {}) {
  return { name, role };
}
createUser(); // { name: 'Guest', role: 'user' }
createUser({ name: "Admin" }); // { name: 'Admin', role: 'user' }
```

## Common Use Cases

### API Response

```js
const { data, status, error } = await fetch(url).then((r) => r.json());
```

### Module Imports

```js
const { useState, useEffect } = require("react");
import { map, filter } from "lodash";
```

### Loop Iteration

```js
const users = [{ name: "John" }, { name: "Jane" }];
for (const { name } of users) {
  console.log(name);
}
```

## Key Points

> Arrays destructure by position, objects by key name

> Use `= value` for defaults

> Use `: newName` to rename object properties

> Rest pattern collects remaining elements

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
