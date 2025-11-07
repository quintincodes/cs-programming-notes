> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Classes

#javascript #programming #javascript #oop #classes

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Classes

## Definition

Classes are templates for creating objects. They encapsulate data with code to work on that data. JavaScript classes are syntactic sugar over prototypes.

## Basic Class Syntax

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    return `Hello, I'm ${this.name}`;
  }
}

const john = new Person("John", 30);
console.log(john.greet()); // "Hello, I'm John"
```

## Class Features

### Constructor

```js
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }
}
```

### Instance Methods

```js
class Rectangle {
  constructor(width, height) {
    this.width = width;
    this.height = height;
  }

  getArea() {
    return this.width * this.height;
  }

  getPerimeter() {
    return 2 * (this.width + this.height);
  }
}
```

### Static Methods

```js
class MathUtils {
  static add(a, b) {
    return a + b;
  }

  static multiply(a, b) {
    return a * b;
  }
}

// Called on class, not instance
MathUtils.add(5, 3); // 8
MathUtils.multiply(4, 2); // 8
```

### Getters and Setters

```js
class Circle {
  constructor(radius) {
    this._radius = radius;
  }

  get radius() {
    return this._radius;
  }

  set radius(value) {
    if (value < 0) throw new Error("Radius must be positive");
    this._radius = value;
  }

  get area() {
    return Math.PI * this._radius ** 2;
  }
}

const circle = new Circle(5);
console.log(circle.area); // 78.54...
circle.radius = 10; // Uses setter
console.log(circle.radius); // Uses getter
```

### Private Fields (ES2022)

```js
class BankAccount {
  #balance = 0; // Private field

  deposit(amount) {
    this.#balance += amount;
  }

  getBalance() {
    return this.#balance;
  }
}

const account = new BankAccount();
account.deposit(100);
account.#balance; // SyntaxError - can't access private field
account.getBalance(); // 100
```

## Inheritance

### extends Keyword

```js
class Animal {
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(name); // Call parent constructor
    this.breed = breed;
  }

  speak() {
    console.log(`${this.name} barks`);
  }
}

const dog = new Dog("Rex", "German Shepherd");
dog.speak(); // "Rex barks"
```

### super Keyword

```js
class Parent {
  greet() {
    return "Hello from Parent";
  }
}

class Child extends Parent {
  greet() {
    return super.greet() + " and Child";
  }
}

new Child().greet(); // "Hello from Parent and Child"
```

## Static Properties and Methods

```js
class User {
  static count = 0;

  constructor(name) {
    this.name = name;
    User.count++;
  }

  static getCount() {
    return User.count;
  }
}

new User("John");
new User("Jane");
User.getCount(); // 2
```

## Class vs Constructor Function

```js
// Constructor function (old way)
function Person(name) {
  this.name = name;
}
Person.prototype.greet = function () {
  return `Hello, ${this.name}`;
};

// Class (modern way)
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    return `Hello, ${this.name}`;
  }
}
```

## instanceof and typeof

```js
class Animal {}
class Dog extends Animal {}

const dog = new Dog();

dog instanceof Dog; // true
dog instanceof Animal; // true
dog instanceof Object; // true

typeof dog; // 'object'
typeof Dog; // 'function'
```

## Common Patterns

### Factory Pattern

```js
class ShapeFactory {
  static create(type, ...args) {
    switch (type) {
      case "circle":
        return new Circle(...args);
      case "rectangle":
        return new Rectangle(...args);
      default:
        throw new Error("Unknown shape");
    }
  }
}
```

### Singleton Pattern

```js
class Database {
  static #instance = null;

  static getInstance() {
    if (!Database.#instance) {
      Database.#instance = new Database();
    }
    return Database.#instance;
  }
}
```

## Key Points

> Classes are syntactic sugar over prototypes

> Always use `new` to create instances

> `super()` must be called before `this` in subclass constructor

> Private fields use # prefix

> Static members belong to class, not instances

## Links

- [MDN Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
