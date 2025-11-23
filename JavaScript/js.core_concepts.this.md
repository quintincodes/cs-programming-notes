> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: this Keyword

#javascript #programming #javascript #core-concepts #this

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# this Keyword

## Definition

`this` refers to the object that is executing the current function. Its value depends on HOW the function is called, not where it's defined.

## this in Different Contexts

### Global Context

```js
console.log(this); // Window (browser) or global (Node)

// Strict mode
("use strict");
console.log(this); // undefined
```

### Object Method

```js
const person = {
  name: "John",
  greet() {
    console.log(this.name); // 'John'
  },
};

person.greet(); // this = person
```

### Regular Function

```js
function showThis() {
  console.log(this);
}

showThis(); // Window (browser) or undefined (strict mode)
```

### Arrow Function

```js
const person = {
  name: "John",
  greet: () => {
    console.log(this.name); // undefined!
  },
  greetProperly() {
    const inner = () => {
      console.log(this.name); // 'John' - inherits from greetProperly
    };
    inner();
  },
};
```

### Constructor Function

```js
function Person(name) {
  this.name = name; // this = new object being created
}

const john = new Person("John");
console.log(john.name); // 'John'
```

### Class

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(`Hello, ${this.name}`);
  }
}

const john = new Person("John");
john.greet(); // 'Hello, John'
```

## Common this Problems

### Problem: Lost this Context

```js
const person = {
  name: "John",
  greet() {
    console.log(this.name);
  },
};

const greet = person.greet;
greet(); // undefined! - this is lost
```

### Problem: Callback Functions

```js
const person = {
  name: "John",
  friends: ["Jane", "Bob"],
  showFriends() {
    this.friends.forEach(function (friend) {
      console.log(`${this.name} knows ${friend}`); // this.name is undefined!
    });
  },
};
```

## Solutions

### Solution 1: Arrow Functions

```js
const person = {
  name: "John",
  friends: ["Jane", "Bob"],
  showFriends() {
    this.friends.forEach((friend) => {
      console.log(`${this.name} knows ${friend}`); // Works!
    });
  },
};
```

### Solution 2: bind()

```js
const person = {
  name: "John",
  greet() {
    console.log(this.name);
  },
};

const boundGreet = person.greet.bind(person);
boundGreet(); // 'John'
```

### Solution 3: call() and apply()

```js
function greet(greeting) {
  console.log(`${greeting}, ${this.name}`);
}

const person = { name: "John" };

greet.call(person, "Hello"); // 'Hello, John'
greet.apply(person, ["Hi"]); // 'Hi, John'
```

### Solution 4: Store this in Variable

```js
const person = {
  name: "John",
  showFriends() {
    const self = this; // Store reference
    this.friends.forEach(function (friend) {
      console.log(`${self.name} knows ${friend}`);
    });
  },
};
```

## call vs apply vs bind

| Method    | Executes?                | Arguments       |
| --------- | ------------------------ | --------------- |
| `call()`  | Yes, immediately         | Comma-separated |
| `apply()` | Yes, immediately         | Array           |
| `bind()`  | No, returns new function | Comma-separated |

```js
function greet(greeting, punctuation) {
  console.log(`${greeting}, ${this.name}${punctuation}`);
}

const person = { name: "John" };

// call - comma separated args
greet.call(person, "Hello", "!"); // 'Hello, John!'

// apply - array of args
greet.apply(person, ["Hi", "?"]); // 'Hi, John?'

// bind - returns new function
const boundGreet = greet.bind(person, "Hey");
boundGreet("."); // 'Hey, John.'
```

## Arrow Functions and this

Arrow functions don't have their own `this`. They inherit `this` from the enclosing scope.

```js
const obj = {
  name: "Object",
  regular: function () {
    console.log(this.name); // 'Object'
  },
  arrow: () => {
    console.log(this.name); // undefined (window.name)
  },
};
```

## Key Points

> this depends on HOW function is called, not WHERE defined

> Arrow functions inherit this from enclosing scope

> Use bind/call/apply to explicitly set this

> In strict mode, this is undefined in regular functions

> In classes, this refers to the instance

## Links

- [MDN this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)
