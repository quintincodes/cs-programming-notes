> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: concat()

#javascript #programming #javascript #methods #arrays

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# concat()

## Definition

The `concat()` method merges two or more arrays into a NEW array. Original arrays remain unchanged.

## Syntax

```js
array.concat(value1, value2, ..., valueN)
```

## Basic Usage

```js
const arr1 = [1, 2];
const arr2 = [3, 4];
const arr3 = [5, 6];

const merged = arr1.concat(arr2);
console.log(merged); // [1, 2, 3, 4]
console.log(arr1); // [1, 2] (unchanged)

// Multiple arrays
const all = arr1.concat(arr2, arr3);
console.log(all); // [1, 2, 3, 4, 5, 6]
```

## Concat Values (Not Just Arrays)

```js
const arr = [1, 2];

const result = arr.concat(3, 4, 5);
console.log(result); // [1, 2, 3, 4, 5]

// Mix arrays and values
const mixed = arr.concat([3, 4], 5, [6, 7]);
console.log(mixed); // [1, 2, 3, 4, 5, 6, 7]
```

## concat() vs Spread Operator

```js
const a = [1, 2];
const b = [3, 4];

// Using concat
const concatResult = a.concat(b);

// Using spread (modern, preferred)
const spreadResult = [...a, ...b];

// Both produce [1, 2, 3, 4]
```

### Performance Comparison

| Method      | Readability | Performance     | Mutates |
| ----------- | ----------- | --------------- | ------- |
| `concat()`  | Good        | Slightly slower | No      |
| `...spread` | Better      | Slightly faster | No      |
| `push()`    | Ok          | Fastest         | Yes     |

## concat() vs push()

```js
const arr = [1, 2];

// concat - returns new array
const newArr = arr.concat([3, 4]);
console.log(arr); // [1, 2] (unchanged)
console.log(newArr); // [1, 2, 3, 4]

// push - modifies original
arr.push(3, 4);
console.log(arr); // [1, 2, 3, 4] (mutated!)
```

## Shallow Copy Behavior

```js
const objects = [{ a: 1 }, { b: 2 }];
const copy = [].concat(objects);

objects[0].a = 99;
console.log(copy[0].a); // 99 (same reference!)
```

## Common Use Cases

### Building Arrays Incrementally

```js
let result = [];
for (const item of items) {
  if (item.valid) {
    result = result.concat(item.values);
  }
}
```

### Flattening One Level

```js
const nested = [
  [1, 2],
  [3, 4],
  [5, 6],
];
const flat = [].concat(...nested);
console.log(flat); // [1, 2, 3, 4, 5, 6]
```

### Creating Copies

```js
const original = [1, 2, 3];
const copy = [].concat(original);
// or: const copy = original.concat();
```

## With Strings

```js
const arr = ["hello"];
const result = arr.concat(" ", "world");
console.log(result); // ['hello', ' ', 'world']
```

## Key Points

> Returns a NEW array, never mutates originals

> Spread operator is often preferred in modern JS

> Only flattens one level (use flat() for deep)

> Shallow copies - objects share references

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)
