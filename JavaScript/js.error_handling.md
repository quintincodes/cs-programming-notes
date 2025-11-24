> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Error Handling

#javascript #programming #javascript #error-handling

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Error Handling

## Definition

Error handling allows you to gracefully handle runtime errors and prevent application crashes.

## try...catch...finally

```js
try {
  // Code that might throw an error
  const data = JSON.parse(invalidJson);
} catch (error) {
  // Handle the error
  console.error("Error:", error.message);
} finally {
  // Always runs, error or not
  console.log("Cleanup complete");
}
```

## Error Object Properties

```js
try {
  throw new Error("Something went wrong");
} catch (error) {
  console.log(error.name); // 'Error'
  console.log(error.message); // 'Something went wrong'
  console.log(error.stack); // Stack trace
}
```

## Built-in Error Types

| Error Type       | When Thrown          |
| ---------------- | -------------------- |
| `Error`          | Generic error        |
| `SyntaxError`    | Invalid syntax       |
| `ReferenceError` | Invalid reference    |
| `TypeError`      | Wrong type operation |
| `RangeError`     | Value out of range   |
| `URIError`       | Invalid URI encoding |

```js
// ReferenceError
console.log(undefinedVar);

// TypeError
null.property;

// RangeError
[].length = -1;

// SyntaxError (at parse time, can't catch)
// eval('if (');
```

## Throwing Errors

### throw Statement

```js
function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }
  return a / b;
}

try {
  divide(10, 0);
} catch (error) {
  console.log(error.message); // 'Cannot divide by zero'
}
```

### Throwing Different Values

```js
// Throw string (not recommended)
throw "An error occurred";

// Throw Error object (recommended)
throw new Error("An error occurred");

// Throw custom error
throw new TypeError("Expected a number");
```

## Custom Errors

```js
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
  }
}

class NetworkError extends Error {
  constructor(message, status) {
    super(message);
    this.name = "NetworkError";
    this.status = status;
  }
}

try {
  throw new ValidationError("Invalid email format");
} catch (error) {
  if (error instanceof ValidationError) {
    console.log("Validation failed:", error.message);
  }
}
```

## Error Handling Patterns

### Re-throwing Errors

```js
try {
  processData(data);
} catch (error) {
  if (error instanceof NetworkError) {
    // Handle network errors
    console.log("Network issue:", error.message);
  } else {
    // Re-throw unknown errors
    throw error;
  }
}
```

### Error Wrapping

```js
try {
  parseConfig(file);
} catch (error) {
  throw new Error(`Config error: ${error.message}`);
}
```

### Optional catch Binding (ES2019)

```js
try {
  doSomething();
} catch {
  // Can omit error parameter if not needed
  console.log("An error occurred");
}
```

## Async Error Handling

### With Promises

```js
fetch("/api/data")
  .then((response) => response.json())
  .catch((error) => {
    console.error("Fetch failed:", error);
  });
```

### With async/await

```js
async function fetchData() {
  try {
    const response = await fetch("/api/data");
    if (!response.ok) {
      throw new Error(`HTTP ${response.status}`);
    }
    return await response.json();
  } catch (error) {
    console.error("Error:", error.message);
    throw error; // Re-throw if needed
  }
}
```

## Global Error Handlers

### Browser

```js
window.onerror = function (message, source, line, col, error) {
  console.log("Global error:", message);
  return true; // Prevents default browser error handling
};

window.addEventListener("unhandledrejection", (event) => {
  console.log("Unhandled promise:", event.reason);
});
```

### Node.js

```js
process.on("uncaughtException", (error) => {
  console.error("Uncaught:", error);
  process.exit(1);
});

process.on("unhandledRejection", (reason, promise) => {
  console.error("Unhandled rejection:", reason);
});
```

## Best Practices

### Be Specific

```js
// Bad - catches everything
try {
  riskyOperation();
} catch (e) {
  console.log("Error");
}

// Good - handle specific errors
try {
  riskyOperation();
} catch (error) {
  if (error instanceof NetworkError) {
    retry();
  } else if (error instanceof ValidationError) {
    showValidationMessage(error.message);
  } else {
    throw error;
  }
}
```

### Don't Swallow Errors

```js
// Bad - error is silently ignored
try {
  doSomething();
} catch (e) {}

// Good - at least log it
try {
  doSomething();
} catch (error) {
  console.error(error);
}
```

## Key Points

> Always use Error objects, not strings

> Be specific about what errors you catch

> Don't swallow errors silently

> Use finally for cleanup operations

> Create custom error classes for domain-specific errors

## Links

- [MDN Error Handling](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Control_flow_and_error_handling)
