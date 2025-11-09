> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Reverse

#javascript #programming #javascript #core-concepts

created: 1737412588691
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!-- #region styles -->

<!-- #endregion -->

## Definition

The `reverse()` method reverses an array in place. The first array element becomes the last, and the last array element becomes the first.

## Syntax

```js
arr.reverse();
```

## Parameters

None

## Return Values

The reversed array.

## Examples

### Basic Array Reversal

```js
const numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers); // [5, 4, 3, 2, 1]

const fruits = ["apple", "banana", "cherry"];
fruits.reverse();
console.log(fruits); // ['cherry', 'banana', 'apple']
```

### String Array Reversal

```js
const words = ["hello", "world", "javascript"];
words.reverse();
console.log(words); // ['javascript', 'world', 'hello']

// Reversing a sentence word order
const sentence = "The quick brown fox".split(" ");
sentence.reverse();
console.log(sentence.join(" ")); // "fox brown quick The"
```

### Mixed Data Types

```js
const mixed = [1, "two", 3, "four", true, null];
mixed.reverse();
console.log(mixed); // [null, true, 'four', 3, 'two', 1]
```

### Working with Objects

```js
const users = [
  { name: "John", age: 30 },
  { name: "Jane", age: 25 },
  { name: "Bob", age: 35 },
];
users.reverse();
console.log(users);
// [
//   { name: 'Bob', age: 35 },
//   { name: 'Jane', age: 25 },
//   { name: 'John', age: 30 }
// ]
```

### Non-Destructive Reversal (Creating Copy)

```js
const original = [1, 2, 3, 4, 5];
const reversed = [...original].reverse();
console.log(original); // [1, 2, 3, 4, 5] (unchanged)
console.log(reversed); // [5, 4, 3, 2, 1]

// Alternative using slice()
const numbers = [10, 20, 30];
const reversedCopy = numbers.slice().reverse();
console.log(numbers); // [10, 20, 30] (unchanged)
console.log(reversedCopy); // [30, 20, 10]
```

### Method Chaining

```js
const numbers = [1, 2, 3, 4, 5];
const result = numbers
  .filter((n) => n % 2 === 0) // [2, 4]
  .reverse() // [4, 2]
  .map((n) => n * 2); // [8, 4]
console.log(result); // [8, 4]
```

### Practical Applications

#### Undo Functionality

```js
class UndoableArray {
  constructor() {
    this.items = [];
    this.history = [];
  }

  push(item) {
    this.history.push([...this.items]);
    this.items.push(item);
  }

  undo() {
    if (this.history.length > 0) {
      this.items = this.history.pop();
    }
  }

  reverseOrder() {
    this.history.push([...this.items]);
    this.items.reverse();
  }
}
```

#### Displaying Recent Items First

```js
const recentActivities = [
  "User logged in",
  "File uploaded",
  "Settings changed",
  "Profile updated",
];

// Show most recent first
const displayOrder = [...recentActivities].reverse();
console.log(displayOrder);
// ['Profile updated', 'Settings changed', 'File uploaded', 'User logged in']
```

## Applicable To

- JavaScript Arrays
- JavaScript Typed Arrays

## Edge Cases

### Empty Arrays

```js
const empty = [];
empty.reverse();
console.log(empty); // [] (no change)
```

### Single Element Arrays

```js
const single = [42];
single.reverse();
console.log(single); // [42] (no change)
```

### Arrays with Undefined/Null

```js
const sparse = [1, undefined, 3, null, 5];
sparse.reverse();
console.log(sparse); // [5, null, 3, undefined, 1]
```

### Edge Case 1

```js
const arr = [1, 2, 3, 4, 5];
arr.reverse();
console.log(arr); // [5, 4, 3, 2, 1]
```

## Links

- [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)

> **Last reviewed**: November 28, 2025
