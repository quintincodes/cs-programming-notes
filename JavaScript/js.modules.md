> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Modules

#javascript #programming #javascript #modules #es6

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Modules

## Definition

Modules allow you to split code into separate files, each with its own scope. You can export and import functionality between modules.

## ES Modules (ESM)

### Named Exports

```js
// math.js
export const PI = 3.14159;

export function add(a, b) {
  return a + b;
}

export function multiply(a, b) {
  return a * b;
}
```

### Named Imports

```js
// app.js
import { PI, add, multiply } from "./math.js";

console.log(PI); // 3.14159
console.log(add(2, 3)); // 5
console.log(multiply(2, 3)); // 6
```

### Rename on Import/Export

```js
// Export with alias
export { add as addition };

// Import with alias
import { add as sum } from "./math.js";
import { multiply as mul } from "./math.js";
```

### Default Export

```js
// user.js
export default class User {
  constructor(name) {
    this.name = name;
  }
}

// Only one default export per file
```

### Default Import

```js
// app.js
import User from "./user.js"; // No curly braces for default

const user = new User("John");
```

### Mixed Exports

```js
// utils.js
export default function main() {}
export function helper() {}
export const VERSION = "1.0";

// Importing
import main, { helper, VERSION } from "./utils.js";
```

### Import All

```js
import * as MathUtils from "./math.js";

MathUtils.add(2, 3);
MathUtils.PI;
```

### Re-exporting

```js
// index.js (barrel file)
export { add, multiply } from "./math.js";
export { default as User } from "./user.js";
export * from "./utils.js";
```

## Dynamic Imports

```js
// Load module on demand
async function loadModule() {
  const module = await import("./heavy-module.js");
  module.doSomething();
}

// With button click
button.addEventListener("click", async () => {
  const { showModal } = await import("./modal.js");
  showModal();
});
```

## CommonJS (Node.js)

### Exporting

```js
// math.js
const add = (a, b) => a + b;
const multiply = (a, b) => a * b;

module.exports = { add, multiply };
// or
module.exports.add = add;
module.exports.multiply = multiply;
```

### Importing

```js
// app.js
const { add, multiply } = require("./math.js");
// or
const math = require("./math.js");
math.add(2, 3);
```

## ESM vs CommonJS

| Feature         | ESM           | CommonJS               |
| --------------- | ------------- | ---------------------- |
| Syntax          | import/export | require/module.exports |
| Loading         | Static        | Dynamic                |
| Async           | Yes           | No                     |
| Tree-shaking    | Yes           | Limited                |
| Browser         | Native        | Bundler needed         |
| Top-level await | Yes           | No                     |

## Using ESM in Browser

```html
<!-- Add type="module" -->
<script type="module" src="app.js"></script>

<!-- Inline module -->
<script type="module">
  import { greet } from "./utils.js";
  greet();
</script>
```

## Using ESM in Node.js

```json
// package.json
{
  "type": "module"
}
```

Or use `.mjs` extension:

```
app.mjs
utils.mjs
```

## Common Patterns

### Barrel Files (index.js)

```js
// components/index.js
export { Button } from "./Button.js";
export { Input } from "./Input.js";
export { Modal } from "./Modal.js";

// Usage
import { Button, Input, Modal } from "./components";
```

### Conditional Imports

```js
let module;
if (isProduction) {
  module = await import("./prod.js");
} else {
  module = await import("./dev.js");
}
```

### Lazy Loading Routes

```js
const routes = {
  "/home": () => import("./pages/Home.js"),
  "/about": () => import("./pages/About.js"),
  "/contact": () => import("./pages/Contact.js"),
};

async function loadPage(path) {
  const module = await routes[path]();
  module.default.render();
}
```

## Key Points

> ESM is the modern standard for JavaScript modules

> Use named exports for multiple exports

> Use default export for main functionality

> Dynamic imports enable code splitting

> CommonJS is still used in Node.js (legacy)

## Links

- [MDN JavaScript Modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
