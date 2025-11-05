> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: async/await

#javascript #programming #javascript #async #async-await

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# async/await

## Definition

`async/await` is syntactic sugar over Promises, making asynchronous code look and behave like synchronous code.

## Basic Syntax

### async Function

```js
async function fetchData() {
  return "data"; // Automatically wrapped in Promise.resolve()
}

// Arrow function
const fetchData = async () => "data";

// Method
const obj = {
  async getData() {
    return "data";
  },
};
```

### await Keyword

```js
async function getUser() {
  const response = await fetch("/api/user");
  const user = await response.json();
  return user;
}
```

## Error Handling

### try/catch

```js
async function fetchData() {
  try {
    const response = await fetch("/api/data");
    if (!response.ok) {
      throw new Error(`HTTP ${response.status}`);
    }
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Error:", error.message);
    throw error; // Re-throw if needed
  }
}
```

### .catch() on Call

```js
async function riskyOperation() {
  throw new Error("Something went wrong");
}

riskyOperation().catch((error) => console.error(error));
```

## Parallel Execution

### Sequential (Slow)

```js
async function sequential() {
  const user = await fetchUser(); // Wait
  const posts = await fetchPosts(); // Then wait
  const comments = await fetchComments(); // Then wait
  return { user, posts, comments };
}
```

### Parallel (Fast)

```js
async function parallel() {
  const [user, posts, comments] = await Promise.all([
    fetchUser(),
    fetchPosts(),
    fetchComments(),
  ]);
  return { user, posts, comments };
}
```

## Common Patterns

### Fetching Data

```js
async function getJSON(url) {
  const response = await fetch(url);
  if (!response.ok) {
    throw new Error(`HTTP ${response.status}`);
  }
  return response.json();
}

// Usage
const data = await getJSON("/api/data");
```

### Sequential Processing

```js
async function processItems(items) {
  const results = [];
  for (const item of items) {
    const result = await processItem(item);
    results.push(result);
  }
  return results;
}
```

### Parallel Processing

```js
async function processItems(items) {
  const results = await Promise.all(items.map((item) => processItem(item)));
  return results;
}
```

### Retry with Delay

```js
async function fetchWithRetry(url, retries = 3, delay = 1000) {
  for (let i = 0; i < retries; i++) {
    try {
      return await fetch(url);
    } catch (error) {
      if (i === retries - 1) throw error;
      await new Promise((r) => setTimeout(r, delay));
    }
  }
}
```

### Timeout Wrapper

```js
async function withTimeout(promise, ms) {
  const timeout = new Promise((_, reject) =>
    setTimeout(() => reject(new Error("Timeout")), ms)
  );
  return Promise.race([promise, timeout]);
}

// Usage
const data = await withTimeout(fetch("/api/data"), 5000);
```

## Top-Level await (ES2022+)

```js
// In ES modules, you can use await at top level
const config = await fetch("/config.json").then((r) => r.json());
console.log(config);
```

## Common Mistakes

### Forgetting await

```js
// Wrong - logs Promise, not data
async function bad() {
  const data = fetch("/api"); // Missing await!
  console.log(data); // Promise { <pending> }
}

// Correct
async function good() {
  const data = await fetch("/api");
  console.log(data);
}
```

### await in forEach (Doesn't Work!)

```js
// Wrong - doesn't wait
items.forEach(async (item) => {
  await processItem(item); // Fire and forget!
});

// Correct - use for...of
for (const item of items) {
  await processItem(item);
}

// Or parallel with Promise.all
await Promise.all(items.map((item) => processItem(item)));
```

## async/await vs .then()

```js
// Promise chain
function getUser() {
  return fetch("/api/user")
    .then((response) => response.json())
    .then((user) => fetch(`/api/posts/${user.id}`))
    .then((response) => response.json());
}

// async/await (cleaner)
async function getUser() {
  const response = await fetch("/api/user");
  const user = await response.json();
  const postsResponse = await fetch(`/api/posts/${user.id}`);
  return postsResponse.json();
}
```

## Key Points

> async functions always return a Promise

> await pauses execution until Promise settles

> Use try/catch for error handling

> Use Promise.all() for parallel operations

> Don't use await in forEach - use for...of

## Links

- [MDN async/await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Promises)
