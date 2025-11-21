> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Splice

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# splice() Method

## Definition

The `splice()` method changes the contents of an array by removing, replacing, or adding elements **in place**.

## Syntax

```js
array.splice(start, deleteCount, item1, item2, ...)
```

- **start**: Index to start changing the array
- **deleteCount**: Number of elements to remove
- **item1, item2, ...**: Elements to add (optional)

## Key Points

> `splice()` MUTATES the original array

> Returns an array of removed elements

> Can remove, add, or replace elements

## Examples

### Remove Elements

```js
const months = ["Jan", "Feb", "March", "April", "May"];
const removed = months.splice(2, 2); // Start at index 2, remove 2 elements

console.log(removed); // ['March', 'April']
console.log(months); // ['Jan', 'Feb', 'May']
```

### Add Elements

```js
const fruits = ["apple", "banana"];
fruits.splice(1, 0, "orange", "mango"); // At index 1, remove 0, add 2

console.log(fruits); // ['apple', 'orange', 'mango', 'banana']
```

### Replace Elements

```js
const colors = ["red", "green", "blue"];
colors.splice(1, 1, "yellow"); // At index 1, remove 1, add 1

console.log(colors); // ['red', 'yellow', 'blue']
```

### Remove from End

```js
const arr = [1, 2, 3, 4, 5];
arr.splice(-2); // Remove last 2 elements

console.log(arr); // [1, 2, 3]
```

## Common Use Cases

### Remove Element by Value

```js
const arr = ["a", "b", "c", "d"];
const index = arr.indexOf("c");
if (index > -1) {
  arr.splice(index, 1);
}
console.log(arr); // ['a', 'b', 'd']
```

### Insert at Specific Position

```js
const tasks = ["task1", "task3"];
tasks.splice(1, 0, "task2"); // Insert 'task2' at index 1
console.log(tasks); // ['task1', 'task2', 'task3']
```

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)
