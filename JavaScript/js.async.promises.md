> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Promises

#javascript #programming #javascript #async #promises

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Promises

## Definition

A Promise represents a value that may be available now, later, or never. It's an object representing the eventual completion or failure of an async operation.

## Promise States

| State         | Description                                   |
| ------------- | --------------------------------------------- |
| **Pending**   | Initial state, neither fulfilled nor rejected |
| **Fulfilled** | Operation completed successfully              |
| **Rejected**  | Operation failed                              |

## Creating a Promise

```js
const myPromise = new Promise((resolve, reject) => {
  // Async operation
  const success = true;

  if (success) {
    resolve("Operation succeeded!");
  } else {
    reject("Operation failed!");
  }
});
```

## Consuming Promises

### .then() and .catch()

```js
myPromise
  .then((result) => {
    console.log(result); // 'Operation succeeded!'
  })
  .catch((error) => {
    console.error(error);
  });
```

### .finally()

```js
myPromise
  .then((result) => console.log(result))
  .catch((error) => console.error(error))
  .finally(() => {
    console.log("Cleanup - runs regardless of outcome");
  });
```

## Chaining Promises

```js
fetch("/api/user")
  .then((response) => response.json())
  .then((user) => fetch(`/api/posts/${user.id}`))
  .then((response) => response.json())
  .then((posts) => console.log(posts))
  .catch((error) => console.error("Error:", error));
```

## Promise Static Methods

### Promise.all()

Wait for ALL promises. Fails fast if any reject.

```js
const promises = [
  fetch("/api/users"),
  fetch("/api/posts"),
  fetch("/api/comments"),
];

Promise.all(promises)
  .then((responses) => Promise.all(responses.map((r) => r.json())))
  .then((data) => {
    const [users, posts, comments] = data;
    console.log(users, posts, comments);
  })
  .catch((error) => console.error("One failed:", error));
```

### Promise.allSettled()

Wait for ALL promises regardless of outcome.

```js
Promise.allSettled([
  Promise.resolve("Success"),
  Promise.reject("Error"),
  Promise.resolve("Another success"),
]).then((results) => {
  results.forEach((result) => {
    if (result.status === "fulfilled") {
      console.log("Value:", result.value);
    } else {
      console.log("Reason:", result.reason);
    }
  });
});
```

### Promise.race()

Returns first settled promise (fulfilled or rejected).

```js
const timeout = new Promise((_, reject) =>
  setTimeout(() => reject("Timeout!"), 5000)
);

Promise.race([fetch("/api/data"), timeout])
  .then((response) => response.json())
  .catch((error) => console.error(error));
```

### Promise.any()

Returns first fulfilled promise. Only rejects if ALL reject.

```js
Promise.any([
  fetch("https://api1.example.com"),
  fetch("https://api2.example.com"),
  fetch("https://api3.example.com"),
])
  .then((response) => console.log("First success:", response))
  .catch((error) => console.log("All failed:", error));
```

## Creating Resolved/Rejected Promises

```js
// Already resolved
const resolved = Promise.resolve("value");

// Already rejected
const rejected = Promise.reject("error");
```

## Common Patterns

### Convert Callback to Promise

```js
function readFilePromise(path) {
  return new Promise((resolve, reject) => {
    fs.readFile(path, (err, data) => {
      if (err) reject(err);
      else resolve(data);
    });
  });
}
```

### Delay/Sleep

```js
const delay = (ms) => new Promise((resolve) => setTimeout(resolve, ms));

delay(2000).then(() => console.log("2 seconds later"));
```

### Retry Logic

```js
async function fetchWithRetry(url, retries = 3) {
  for (let i = 0; i < retries; i++) {
    try {
      return await fetch(url);
    } catch (error) {
      if (i === retries - 1) throw error;
      await delay(1000 * (i + 1)); // Exponential backoff
    }
  }
}
```

## Comparison Table

| Method         | Resolves When  | Rejects When  |
| -------------- | -------------- | ------------- |
| `all()`        | All fulfill    | Any rejects   |
| `allSettled()` | All settle     | Never         |
| `race()`       | First settles  | First rejects |
| `any()`        | First fulfills | All reject    |

## Key Points

> Promises are immutable once settled

> Always return/throw in .then() for proper chaining

> Use .catch() at the end of chains

> Prefer async/await for cleaner code

## Links

- [MDN Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
