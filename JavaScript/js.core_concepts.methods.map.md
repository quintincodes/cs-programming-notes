> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Map

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# map() Method

## Definition

The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.

## Syntax

```js
const newArray = array.map(callback(currentValue, index, array), thisArg);
```

## Parameters

- **callback**: Function that produces an element of the new array
  - **currentValue**: The current element being processed
  - **index** (optional): The index of the current element
  - **array** (optional): The array map was called upon
- **thisArg** (optional): Value to use as `this` when executing callback

## Return Value

A new array with each element being the result of the callback function.

## Key Points

> `map()` does NOT mutate the original array - it returns a new array

> Always return a value from the callback, otherwise you get `undefined`

> `map()` is chainable with other array methods like `filter()` and `reduce()`

## Examples

### Basic Transformation

```js
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map((num) => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]
```

### Extracting Object Properties

```js
const users = [
  { name: "John", age: 30 },
  { name: "Jane", age: 25 },
  { name: "Bob", age: 35 },
];
const names = users.map((user) => user.name);
console.log(names); // ['John', 'Jane', 'Bob']
```

## Common Use Cases

1. **Data transformation** - Converting data from one format to another
2. **React rendering** - Mapping arrays to JSX elements
3. **API response processing** - Extracting specific fields from responses

## map() vs forEach()

| map()                 | forEach()            |
| --------------------- | -------------------- |
| Returns new array     | Returns undefined    |
| Chainable             | Not chainable        |
| Use when transforming | Use for side effects |

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)
