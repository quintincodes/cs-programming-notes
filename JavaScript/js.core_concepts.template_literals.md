> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Template Literals

#javascript #programming #javascript #core-concepts

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Template Literals

## Definition

Template literals are string literals allowing embedded expressions, multi-line strings, and string interpolation. They use backticks (`) instead of quotes.

## Syntax

```js
`string text``string text ${expression} more text``multi
line
string`;
```

## String Interpolation

```js
const name = "John";
const age = 30;

// Old way (concatenation)
const old = "Hello, " + name + "! You are " + age + " years old.";

// Template literal
const modern = `Hello, ${name}! You are ${age} years old.`;
```

## Expressions Inside ${}

```js
const a = 5;
const b = 10;

console.log(`Sum: ${a + b}`); // Sum: 15
console.log(`Result: ${a > b ? "a" : "b"}`); // Result: b
console.log(`Upper: ${name.toUpperCase()}`); // Upper: JOHN
```

## Multi-line Strings

```js
// Old way
const oldMulti = "Line 1\n" + "Line 2\n" + "Line 3";

// Template literal
const newMulti = `Line 1
Line 2
Line 3`;
```

## Nested Templates

```js
const isAdmin = true;
const message = `User is ${isAdmin ? `an admin` : `a regular user`}`;
```

## Common Use Cases

### HTML Templates

```js
const user = { name: "John", role: "Admin" };
const html = `
    <div class="user-card">
        <h2>${user.name}</h2>
        <p>Role: ${user.role}</p>
    </div>
`;
```

### Building URLs

```js
const baseUrl = "https://api.example.com";
const userId = 123;
const url = `${baseUrl}/users/${userId}/profile`;
```

### Logging

```js
const item = { name: "Widget", price: 9.99 };
console.log(`Processing ${item.name} - $${item.price}`);
```

## Key Points

> Use backticks ` not quotes ' or "

> Expressions go inside `${}`

> Preserves whitespace and newlines

> Can nest template literals

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals)
