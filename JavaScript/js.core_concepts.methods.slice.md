> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Slice

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# slice() Method

## Definition

The `slice()` method returns a shallow copy of a portion of an array or string into a new array/string, without modifying the original.

## Syntax

```js
array.slice(start, end);
string.slice(start, end);
```

- **start**: Index to begin extraction (inclusive)
- **end**: Index to end extraction (exclusive) - optional

## Key Points

> `slice()` does NOT mutate the original array/string

> End index is NOT included in the result

> Negative indices count from the end

## Array Examples

### Basic Slicing

```js
const fruits = ["apple", "banana", "cherry", "date", "elderberry"];

console.log(fruits.slice(1, 3)); // ['banana', 'cherry']
console.log(fruits.slice(2)); // ['cherry', 'date', 'elderberry']
console.log(fruits.slice(-2)); // ['date', 'elderberry']
console.log(fruits.slice(1, -1)); // ['banana', 'cherry', 'date']
```

### Copy Entire Array

```js
const original = [1, 2, 3];
const copy = original.slice();
// or: const copy = [...original];
```

## String Examples

```js
const str = "Hello World";

console.log(str.slice(0, 5)); // 'Hello'
console.log(str.slice(6)); // 'World'
console.log(str.slice(-5)); // 'World'
```

## slice() vs splice()

| slice()                  | splice()                     |
| ------------------------ | ---------------------------- |
| Does NOT modify original | MODIFIES original            |
| Returns new array        | Returns removed elements     |
| For copying portions     | For adding/removing elements |

```js
const arr = [1, 2, 3, 4, 5];

// slice - original unchanged
const sliced = arr.slice(1, 3); // [2, 3]
console.log(arr); // [1, 2, 3, 4, 5]

// splice - original modified
const spliced = arr.splice(1, 2); // [2, 3]
console.log(arr); // [1, 4, 5]
```

## Links

- [MDN Array.slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)
- [MDN String.slice()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
