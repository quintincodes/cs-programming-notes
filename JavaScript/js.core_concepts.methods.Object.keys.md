> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Object.keys(), values(), entries()

#javascript #programming #javascript #methods #objects

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Object.keys(), values(), entries()

## Definition

Static methods to extract keys, values, or key-value pairs from an object as arrays.

## Syntax

```js
Object.keys(obj); // Returns array of keys
Object.values(obj); // Returns array of values
Object.entries(obj); // Returns array of [key, value] pairs
```

## Object.keys()

```js
const person = { name: "John", age: 30, city: "NYC" };

const keys = Object.keys(person);
console.log(keys); // ['name', 'age', 'city']

// Iterate over keys
Object.keys(person).forEach((key) => {
  console.log(`${key}: ${person[key]}`);
});
```

## Object.values()

```js
const person = { name: "John", age: 30, city: "NYC" };

const values = Object.values(person);
console.log(values); // ['John', 30, 'NYC']

// Sum numeric values
const scores = { math: 90, english: 85, science: 88 };
const total = Object.values(scores).reduce((a, b) => a + b, 0);
console.log(total); // 263
```

## Object.entries()

```js
const person = { name: "John", age: 30 };

const entries = Object.entries(person);
console.log(entries); // [['name', 'John'], ['age', 30]]

// Destructuring in loop
for (const [key, value] of Object.entries(person)) {
  console.log(`${key}: ${value}`);
}
```

## Comparison

| Method      | Returns                   | Use Case                 |
| ----------- | ------------------------- | ------------------------ |
| `keys()`    | `['key1', 'key2']`        | Need only property names |
| `values()`  | `['val1', 'val2']`        | Need only values         |
| `entries()` | `[['key1', 'val1'], ...]` | Need both                |

## Converting Back to Object

```js
// Object.fromEntries() - reverse of entries()
const entries = [
  ["name", "John"],
  ["age", 30],
];
const obj = Object.fromEntries(entries);
console.log(obj); // { name: 'John', age: 30 }
```

## Common Use Cases

### Transform Object Values

```js
const prices = { apple: 1, banana: 2, orange: 3 };

// Double all prices
const doubled = Object.fromEntries(
  Object.entries(prices).map(([key, value]) => [key, value * 2])
);
console.log(doubled); // { apple: 2, banana: 4, orange: 6 }
```

### Filter Object Properties

```js
const data = { name: "John", age: 30, password: "secret" };

// Remove sensitive fields
const safe = Object.fromEntries(
  Object.entries(data).filter(([key]) => key !== "password")
);
console.log(safe); // { name: 'John', age: 30 }
```

### Count Properties

```js
const obj = { a: 1, b: 2, c: 3 };
const count = Object.keys(obj).length;
console.log(count); // 3
```

### Check if Object is Empty

```js
const isEmpty = (obj) => Object.keys(obj).length === 0;

isEmpty({}); // true
isEmpty({ a: 1 }); // false
```

### Convert to Map

```js
const obj = { a: 1, b: 2 };
const map = new Map(Object.entries(obj));
console.log(map.get("a")); // 1
```

### Swap Keys and Values

```js
const obj = { a: 1, b: 2, c: 3 };
const swapped = Object.fromEntries(Object.entries(obj).map(([k, v]) => [v, k]));
console.log(swapped); // { 1: 'a', 2: 'b', 3: 'c' }
```

## Only Own Enumerable Properties

```js
// These methods only return own enumerable properties
const parent = { inherited: true };
const child = Object.create(parent);
child.own = "value";

Object.keys(child); // ['own'] - not inherited
```

## Key Points

> Only returns own enumerable properties

> Returns arrays, not iterators

> Use Object.fromEntries() to convert back

> Order matches insertion order (ES2015+)

## Links

- [MDN Object.keys()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
- [MDN Object.values()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/values)
- [MDN Object.entries()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
