> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: indexOf() and lastIndexOf()

#javascript #programming #javascript #methods #arrays #strings

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# indexOf() and lastIndexOf()

## Definition

`indexOf()` returns the FIRST index where an element is found. `lastIndexOf()` returns the LAST index. Both return -1 if not found.

## Syntax

```js
array.indexOf(searchElement, fromIndex);
array.lastIndexOf(searchElement, fromIndex);
string.indexOf(searchString, fromIndex);
string.lastIndexOf(searchString, fromIndex);
```

## Array indexOf()

```js
const fruits = ["apple", "banana", "cherry", "banana"];

fruits.indexOf("banana"); // 1 (first occurrence)
fruits.indexOf("grape"); // -1 (not found)
fruits.indexOf("banana", 2); // 3 (search from index 2)
```

## Array lastIndexOf()

```js
const fruits = ["apple", "banana", "cherry", "banana"];

fruits.lastIndexOf("banana"); // 3 (last occurrence)
fruits.lastIndexOf("banana", 2); // 1 (search backwards from index 2)
```

## String indexOf()

```js
const str = "Hello World, Hello Universe";

str.indexOf("Hello"); // 0
str.indexOf("Hello", 1); // 13 (search from index 1)
str.indexOf("hello"); // -1 (case-sensitive!)
str.indexOf("xyz"); // -1
```

## String lastIndexOf()

```js
const str = "Hello World, Hello Universe";

str.lastIndexOf("Hello"); // 13
str.lastIndexOf("o"); // 22
str.lastIndexOf("o", 10); // 7 (search backwards from index 10)
```

## indexOf() vs includes()

```js
const arr = [1, 2, 3, NaN];

// indexOf - returns position
arr.indexOf(2); // 1
arr.indexOf(99); // -1

// includes - returns boolean
arr.includes(2); // true
arr.includes(99); // false

// Key difference: NaN handling
arr.indexOf(NaN); // -1 (can't find NaN!)
arr.includes(NaN); // true (can find NaN)
```

### When to Use Which

| Use Case                | Method          |
| ----------------------- | --------------- |
| Need position           | `indexOf()`     |
| Just checking existence | `includes()`    |
| Need to find NaN        | `includes()`    |
| Need last position      | `lastIndexOf()` |

## Common Patterns

### Check if Exists

```js
// Old way
if (arr.indexOf(item) !== -1) { ... }
if (arr.indexOf(item) > -1) { ... }
if (~arr.indexOf(item)) { ... }  // bitwise trick

// Modern way (preferred)
if (arr.includes(item)) { ... }
```

### Find and Remove

```js
const arr = ["a", "b", "c"];
const index = arr.indexOf("b");
if (index !== -1) {
  arr.splice(index, 1);
}
console.log(arr); // ['a', 'c']
```

### Count Occurrences

```js
function countOccurrences(str, search) {
  let count = 0;
  let pos = str.indexOf(search);
  while (pos !== -1) {
    count++;
    pos = str.indexOf(search, pos + 1);
  }
  return count;
}
countOccurrences("hello world hello", "hello"); // 2
```

### Find All Indexes

```js
function findAllIndexes(arr, value) {
  const indexes = [];
  let idx = arr.indexOf(value);
  while (idx !== -1) {
    indexes.push(idx);
    idx = arr.indexOf(value, idx + 1);
  }
  return indexes;
}
findAllIndexes([1, 2, 1, 3, 1], 1); // [0, 2, 4]
```

## Strict Equality

```js
const arr = [1, "1", true];

arr.indexOf(1); // 0
arr.indexOf("1"); // 1 (different from number 1)
arr.indexOf(true); // 2
arr.indexOf("true"); // -1 (string !== boolean)
```

## Key Points

> Returns -1 when not found

> Uses strict equality (===)

> Case-sensitive for strings

> Cannot find NaN (use includes() instead)

## Links

- [MDN indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)
- [MDN lastIndexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)
