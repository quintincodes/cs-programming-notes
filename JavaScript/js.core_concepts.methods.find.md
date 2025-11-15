> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Find

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# find() and findIndex() Methods

## find() Method

Returns the **first element** in the array that satisfies the provided testing function. Returns `undefined` if no element is found.

```js
const numbers = [5, 12, 8, 130, 44];
const found = numbers.find((num) => num > 10);
console.log(found); // 12
```

## findIndex() Method

Returns the **index** of the first element that satisfies the testing function. Returns `-1` if no element is found.

```js
const numbers = [5, 12, 8, 130, 44];
const index = numbers.findIndex((num) => num > 10);
console.log(index); // 1
```

## Key Differences

| find()                           | findIndex()               |
| -------------------------------- | ------------------------- |
| Returns the element              | Returns the index         |
| Returns `undefined` if not found | Returns `-1` if not found |

## Common Use Cases

### Find Object by Property

```js
const users = [
  { id: 1, name: "John" },
  { id: 2, name: "Jane" },
  { id: 3, name: "Bob" },
];

const user = users.find((u) => u.id === 2);
console.log(user); // { id: 2, name: 'Jane' }
```

### Check if Element Exists

```js
const fruits = ["apple", "banana", "orange"];
const hasBanana = fruits.find((f) => f === "banana") !== undefined;
// Or use includes(): fruits.includes('banana')
```

## find() vs filter()

| find()                   | filter()            |
| ------------------------ | ------------------- |
| Returns first match only | Returns all matches |
| Returns single element   | Returns array       |
| Stops after first match  | Checks all elements |

## Links

- [MDN find()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
- [MDN findIndex()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)
