> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Push

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# push() and unshift() Methods

## push() - Add to End

Adds one or more elements to the **end** of an array and returns the new length.

```js
const fruits = ["apple", "banana"];
const newLength = fruits.push("orange");

console.log(fruits); // ['apple', 'banana', 'orange']
console.log(newLength); // 3
```

### Push Multiple Elements

```js
const arr = [1, 2];
arr.push(3, 4, 5);
console.log(arr); // [1, 2, 3, 4, 5]
```

## unshift() - Add to Beginning

Adds one or more elements to the **beginning** of an array and returns the new length.

```js
const fruits = ["banana", "orange"];
fruits.unshift("apple");

console.log(fruits); // ['apple', 'banana', 'orange']
```

## Comparison Table

| Method      | Position            | Returns         | Mutates |
| ----------- | ------------------- | --------------- | ------- |
| `push()`    | End                 | New length      | Yes     |
| `unshift()` | Beginning           | New length      | Yes     |
| `pop()`     | End (removes)       | Removed element | Yes     |
| `shift()`   | Beginning (removes) | Removed element | Yes     |

## Performance Note

> `push()` is faster than `unshift()` because adding to end doesn't require re-indexing

## Common Patterns

### Building Arrays

```js
const results = [];
for (let i = 0; i < 5; i++) {
  results.push(i * 2);
}
console.log(results); // [0, 2, 4, 6, 8]
```

### Queue Implementation

```js
const queue = [];
queue.push("first"); // Add to end
queue.push("second");
const next = queue.shift(); // Remove from beginning
console.log(next); // 'first'
```

## Links

- [MDN push()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)
- [MDN unshift()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)
