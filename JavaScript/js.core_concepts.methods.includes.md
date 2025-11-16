> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Includes

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# includes() Method

## Definition

The `includes()` method determines whether an array or string contains a certain value, returning `true` or `false`.

## Array includes()

```js
const fruits = ["apple", "banana", "mango"];

console.log(fruits.includes("banana")); // true
console.log(fruits.includes("grape")); // false
```

### With fromIndex Parameter

```js
const numbers = [1, 2, 3, 4, 5];
console.log(numbers.includes(3, 3)); // false (starts searching from index 3)
console.log(numbers.includes(4, 3)); // true
```

## String includes()

```js
const sentence = "The quick brown fox jumps over the lazy dog";

console.log(sentence.includes("quick")); // true
console.log(sentence.includes("Quick")); // false (case-sensitive!)
```

## Key Points

> `includes()` is case-sensitive for strings

> Returns boolean (`true`/`false`), not the element or index

> Uses strict equality (`===`) for comparison

> `NaN` is handled correctly: `[NaN].includes(NaN)` returns `true`

## includes() vs indexOf()

| includes()                         | indexOf()                     |
| ---------------------------------- | ----------------------------- |
| Returns `true`/`false`             | Returns index or `-1`         |
| Finds `NaN` correctly              | Cannot find `NaN`             |
| More readable for existence checks | Better when you need position |

```js
const arr = [1, 2, NaN];

// includes handles NaN
arr.includes(NaN); // true

// indexOf cannot find NaN
arr.indexOf(NaN); // -1
```

## Common Use Cases

### Conditional Logic

```js
const roles = ["admin", "editor", "viewer"];

if (roles.includes("admin")) {
  console.log("Has admin access");
}
```

### Input Validation

```js
const validOptions = ["small", "medium", "large"];
const userInput = "medium";

if (!validOptions.includes(userInput)) {
  throw new Error("Invalid option");
}
```

## Links

- [MDN Array.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
- [MDN String.includes()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
