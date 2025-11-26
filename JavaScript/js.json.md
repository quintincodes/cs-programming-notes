> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: JSON

#javascript #programming #javascript #json #data

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# JSON

## Definition

JSON (JavaScript Object Notation) is a lightweight data format for storing and exchanging data. It's language-independent but uses JavaScript syntax.

## JSON Syntax

```json
{
  "name": "John",
  "age": 30,
  "isStudent": false,
  "courses": ["Math", "Science"],
  "address": {
    "city": "NYC",
    "zip": "10001"
  },
  "spouse": null
}
```

## JSON Data Types

| Type    | Example                            |
| ------- | ---------------------------------- |
| String  | `"hello"` (must use double quotes) |
| Number  | `42`, `3.14`, `-1`                 |
| Boolean | `true`, `false`                    |
| null    | `null`                             |
| Array   | `[1, 2, 3]`                        |
| Object  | `{"key": "value"}`                 |

**NOT allowed**: functions, undefined, dates, comments

## JSON.parse()

Convert JSON string to JavaScript object.

```js
const jsonString = '{"name": "John", "age": 30}';
const obj = JSON.parse(jsonString);

console.log(obj.name); // "John"
console.log(obj.age); // 30
```

### With Reviver Function

```js
const json = '{"date": "2024-01-15"}';

const obj = JSON.parse(json, (key, value) => {
  if (key === "date") {
    return new Date(value);
  }
  return value;
});

console.log(obj.date); // Date object
```

## JSON.stringify()

Convert JavaScript object to JSON string.

```js
const obj = { name: "John", age: 30 };
const jsonString = JSON.stringify(obj);

console.log(jsonString); // '{"name":"John","age":30}'
```

### Pretty Print

```js
const obj = { name: "John", age: 30 };

// Second param: replacer, Third param: spaces
const pretty = JSON.stringify(obj, null, 2);
console.log(pretty);
// {
//   "name": "John",
//   "age": 30
// }
```

### With Replacer Function

```js
const user = { name: "John", password: "secret", age: 30 };

// Filter out sensitive data
const json = JSON.stringify(user, (key, value) => {
  if (key === "password") return undefined;
  return value;
});

console.log(json); // '{"name":"John","age":30}'
```

### With Replacer Array

```js
const user = { name: "John", age: 30, city: "NYC" };

// Only include specific keys
const json = JSON.stringify(user, ["name", "age"]);
console.log(json); // '{"name":"John","age":30}'
```

## Common Operations

### Deep Clone

```js
const original = { a: 1, b: { c: 2 } };
const clone = JSON.parse(JSON.stringify(original));

clone.b.c = 99;
console.log(original.b.c); // 2 (unchanged)
```

**Warning**: Loses functions, undefined, Dates, Maps, Sets, etc.

### Check Valid JSON

```js
function isValidJSON(str) {
  try {
    JSON.parse(str);
    return true;
  } catch (e) {
    return false;
  }
}

isValidJSON('{"name": "John"}'); // true
isValidJSON('{name: "John"}'); // false (missing quotes)
```

### Fetch JSON

```js
async function getData() {
  const response = await fetch("/api/data");
  const data = await response.json(); // Parses JSON
  return data;
}
```

### LocalStorage

```js
// Save
const user = { name: "John", age: 30 };
localStorage.setItem("user", JSON.stringify(user));

// Load
const saved = JSON.parse(localStorage.getItem("user"));
console.log(saved.name); // "John"
```

## toJSON() Method

Custom serialization for objects.

```js
const user = {
  name: "John",
  password: "secret",
  toJSON() {
    return { name: this.name }; // Exclude password
  },
};

JSON.stringify(user); // '{"name":"John"}'
```

## Common Gotchas

### Circular References

```js
const obj = { name: "John" };
obj.self = obj; // Circular reference

JSON.stringify(obj); // TypeError: Converting circular structure to JSON
```

### Date Handling

```js
const obj = { date: new Date() };
const json = JSON.stringify(obj);
// '{"date":"2024-01-15T10:30:00.000Z"}'

const parsed = JSON.parse(json);
console.log(parsed.date); // String, not Date!

// Need to convert back
parsed.date = new Date(parsed.date);
```

### Special Numbers

```js
JSON.stringify({ a: NaN, b: Infinity });
// '{"a":null,"b":null}'
```

## Key Points

> Use double quotes for strings in JSON

> JSON.parse() converts string to object

> JSON.stringify() converts object to string

> Functions and undefined are not valid JSON

> Dates become strings when stringified

## Links

- [MDN JSON](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON)
