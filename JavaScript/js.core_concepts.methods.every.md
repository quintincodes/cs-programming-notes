> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: every() and some()

#javascript #programming #javascript #methods #arrays

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# every() and some()

## Definition

`every()` tests whether ALL elements pass a condition. `some()` tests whether AT LEAST ONE element passes.

## Syntax

```js
array.every(callback(element, index, array));
array.some(callback(element, index, array));
```

## every() - All Must Pass

```js
const numbers = [2, 4, 6, 8];

// Check if all are even
const allEven = numbers.every((num) => num % 2 === 0);
console.log(allEven); // true

// Check if all are less than 10
const allSmall = numbers.every((num) => num < 10);
console.log(allSmall); // true

// Check if all are greater than 5
const allBig = numbers.every((num) => num > 5);
console.log(allBig); // false (2 and 4 fail)
```

## some() - At Least One Must Pass

```js
const numbers = [1, 3, 5, 8];

// Check if any is even
const hasEven = numbers.some((num) => num % 2 === 0);
console.log(hasEven); // true (8 is even)

// Check if any is greater than 10
const hasBig = numbers.some((num) => num > 10);
console.log(hasBig); // false

// Check if any is negative
const hasNegative = numbers.some((num) => num < 0);
console.log(hasNegative); // false
```

## Comparison

| Method    | Returns true when  | Short-circuits         |
| --------- | ------------------ | ---------------------- |
| `every()` | ALL elements pass  | Stops at first failure |
| `some()`  | ANY element passes | Stops at first success |

## Common Use Cases

### Form Validation

```js
const fields = ["name", "email", "password"];
const formData = { name: "John", email: "j@e.com", password: "123" };

const allFilled = fields.every((field) => formData[field]?.length > 0);
console.log(allFilled); // true
```

### Permission Check

```js
const userPermissions = ["read", "write"];
const required = ["read", "write", "delete"];

const hasAll = required.every((p) => userPermissions.includes(p));
console.log(hasAll); // false (missing 'delete')
```

### Check for Bad Data

```js
const data = [10, 20, null, 40];

const hasMissing = data.some((item) => item === null || item === undefined);
console.log(hasMissing); // true
```

### Age Verification

```js
const ages = [21, 25, 18, 30];

const allAdults = ages.every((age) => age >= 18);
console.log(allAdults); // true

const hasMinor = ages.some((age) => age < 18);
console.log(hasMinor); // false
```

## With Objects

```js
const users = [
  { name: "John", active: true },
  { name: "Jane", active: true },
  { name: "Bob", active: false },
];

const allActive = users.every((u) => u.active); // false
const someActive = users.some((u) => u.active); // true
```

## Empty Array Behavior

```js
[].every((x) => x > 0); // true (vacuously true)
[].some((x) => x > 0); // false
```

## Key Points

> `every()` returns true for empty arrays (vacuous truth)

> `some()` returns false for empty arrays

> Both short-circuit for performance

> Return boolean, not array

## Links

- [MDN every()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)
- [MDN some()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)
