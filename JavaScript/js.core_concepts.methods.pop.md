> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Pop

#javascript #programming #javascript #core-concepts

created: 1738107296077
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## Definition

The `pop()` method removes the last element from an array and returns that element. This method changes the length of the array.

## Syntax

```js
arr.pop();
```

## Parameters

None

## Return Values

The removed element from the array.

## Examples

### Basic Array Pop

```js
const fruits = ["apple", "banana", "cherry", "date"];
const lastFruit = fruits.pop();

console.log(lastFruit); // 'date'
console.log(fruits); // ['apple', 'banana', 'cherry']
console.log(fruits.length); // 3
```

### Pop with Numbers

```js
const numbers = [10, 20, 30, 40, 50];
const removed = numbers.pop();

console.log(removed); // 50
console.log(numbers); // [10, 20, 30, 40]
```

### Using Pop in Loops

```js
const tasks = ["task1", "task2", "task3", "task4"];

while (tasks.length > 0) {
  const currentTask = tasks.pop();
  console.log(`Processing: ${currentTask}`);
}
// Output:
// Processing: task4
// Processing: task3
// Processing: task2
// Processing: task1

console.log(tasks); // [] (empty array)
```

### Pop with Return Value Checking

```js
const stack = [1, 2, 3];

// Safe popping with length check
if (stack.length > 0) {
  const item = stack.pop();
  console.log(`Removed: ${item}`); // Removed: 3
} else {
  console.log("Stack is empty");
}
```

### Building a Stack Data Structure

```js
class Stack {
  constructor() {
    this.items = [];
  }

  push(item) {
    this.items.push(item);
  }

  pop() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items.pop();
  }

  peek() {
    if (this.isEmpty()) {
      return null;
    }
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }
}

const stack = new Stack();
stack.push("first");
stack.push("second");
stack.push("third");

console.log(stack.pop()); // 'third'
console.log(stack.peek()); // 'second'
console.log(stack.size()); // 2
```

### Undo Functionality

```js
class EditHistory {
  constructor() {
    this.history = [];
  }

  saveState(state) {
    this.history.push(state);
  }

  undo() {
    if (this.history.length > 1) {
      this.history.pop(); // Remove current state
      return this.history[this.history.length - 1]; // Return previous state
    }
    return null;
  }

  getCurrentState() {
    return this.history[this.history.length - 1] || null;
  }
}

const editor = new EditHistory();
editor.saveState("Initial text");
editor.saveState("Added paragraph");
editor.saveState("Fixed typo");

console.log(editor.getCurrentState()); // 'Fixed typo'
const previousState = editor.undo();
console.log(previousState); // 'Added paragraph'
```

### Processing Array Elements Backwards

```js
const messages = ["Hello", "World", "JavaScript", "Rocks"];
const processedMessages = [];

// Process from last to first
while (messages.length > 0) {
  const message = messages.pop();
  processedMessages.push(message.toUpperCase());
}

console.log(processedMessages); // ['ROCKS', 'JAVASCRIPT', 'WORLD', 'HELLO']
```

### Pop with Object Arrays

```js
const users = [
  { id: 1, name: "John" },
  { id: 2, name: "Jane" },
  { id: 3, name: "Bob" },
];

const lastUser = users.pop();
console.log(lastUser); // { id: 3, name: 'Bob' }
console.log(users.length); // 2

// Extract specific property
const priorities = [
  { task: "Email", priority: 1 },
  { task: "Meeting", priority: 2 },
  { task: "Report", priority: 3 },
];

const highestPriority = priorities.pop();
console.log(`Next task: ${highestPriority.task}`); // Next task: Report
```

### Combining Pop with Other Methods

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

// Remove last 3 elements
const removedElements = [];
for (let i = 0; i < 3; i++) {
  if (numbers.length > 0) {
    removedElements.push(numbers.pop());
  }
}

console.log(numbers); // [1, 2, 3, 4, 5, 6, 7]
console.log(removedElements); // [10, 9, 8]

// Method chaining with conditional pop
const data = [1, 2, 3, 4, 5];
const result = data
  .filter((n) => n % 2 === 0) // [2, 4]
  .map((n) => n * 2) // [4, 8]
  .slice(); // Create copy for safe popping

const lastEven = result.pop(); // 8
console.log(lastEven); // 8
console.log(result); // [4]
```

## Edge Cases

### Empty Array

```js
const emptyArray = [];
const result = emptyArray.pop();

console.log(result); // undefined
console.log(emptyArray); // [] (still empty)
console.log(emptyArray.length); // 0
```

### Single Element Array

```js
const singleElement = ["only"];
const removed = singleElement.pop();

console.log(removed); // 'only'
console.log(singleElement); // []
console.log(singleElement.length); // 0
```

### Arrays with Special Values

```js
const specialValues = [undefined, null, "", 0, false];
console.log(specialValues.pop()); // false
console.log(specialValues.pop()); // 0
console.log(specialValues.pop()); // ''
console.log(specialValues.pop()); // null
console.log(specialValues.pop()); // undefined
console.log(specialValues.pop()); // undefined (array is now empty)
```

### Sparse Arrays

```js
const sparse = [1, , , 4]; // Array with holes
console.log(sparse.length); // 4
const last = sparse.pop();
console.log(last); // 4
console.log(sparse.length); // 3
console.log(sparse); // [1, , ,] (still has holes)
```

## Best Practices

1. **Check array length before popping**:

```js
if (array.length > 0) {
  const item = array.pop();
  // Process item
}
```

2. **Store return value when needed**:

```js
const removed = array.pop(); // Don't ignore return value if you need it
```

3. **Use pop for LIFO (Last In, First Out) operations**:

```js
// Stack-like behavior
stack.push(item); // Add to end
const item = stack.pop(); // Remove from end
```

4. **Consider alternatives for other use cases**:

```js
// To remove first element, use shift()
const first = array.shift();

// To remove element at specific index, use splice()
const removed = array.splice(index, 1)[0];
```

The `pop()` method is essential for implementing stack data structures and processing arrays in reverse order while modifying the original array.

```js
const arr = ["apple", "banana", "cherry", "date"];
const removedElement = arr.pop();

console.log(removedElement); // 'date'
console.log(arr); // ['apple', 'banana', 'cherry']
```

## Applicable To

- Arrays
- Typed Arrays

## Edge Cases

> **Last reviewed**: November 28, 2025

## Links
