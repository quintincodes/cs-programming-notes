> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Filter

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# filter() Method

## Definition

The `filter()` method creates a shallow copy of a portion of an array, filtered down to just the elements that pass the test implemented by the provided function.

## Syntax

```js
const newArray = array.filter(callback(element, index, array), thisArg);
```

## Parameters

- **callback**: Function to test each element (should return true/false)
  - **element**: The current element being processed
  - **index** (optional): The index of the current element
  - **array** (optional): The array filter was called upon
- **thisArg** (optional): Value to use as `this` when executing callback

## Return Value

A new array with elements that pass the test. If no elements pass, an empty array is returned.

## Key Points

> `filter()` does NOT mutate the original array

> The callback must return a truthy/falsy value

> Returns empty array `[]` if no elements pass the test

## Examples

### Filter Numbers

```js
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const evens = numbers.filter((num) => num % 2 === 0);
console.log(evens); // [2, 4, 6, 8, 10]
```

### Filter Objects

```js
const users = [
  { name: "John", age: 30, active: true },
  { name: "Jane", age: 25, active: false },
  { name: "Bob", age: 35, active: true },
];
const activeUsers = users.filter((user) => user.active);
// [{ name: 'John', age: 30, active: true }, { name: 'Bob', age: 35, active: true }]
```

### Remove Falsy Values

```js
const mixed = [0, 1, false, 2, "", 3, null, undefined, 4, NaN, 5];
const truthy = mixed.filter(Boolean);
console.log(truthy); // [1, 2, 3, 4, 5]
```

### Search/Filter Strings

```js
const fruits = ["apple", "banana", "grape", "mango", "orange"];
const search = fruits.filter((fruit) => fruit.includes("an"));
console.log(search); // ['banana', 'mango', 'orange']
```

## Chaining with map()

```js
const users = [
  { name: "John", age: 30 },
  { name: "Jane", age: 17 },
  { name: "Bob", age: 25 },
];

const adultNames = users
  .filter((user) => user.age >= 18)
  .map((user) => user.name);
console.log(adultNames); // ['John', 'Bob']
```

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)
