> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Fetch API

#javascript #programming #javascript #fetch #api

created: 1732400000000
updated: 1732400000000

---

<!--#region styles-->

<!--#endregion-->

# Fetch API

## Definition

The Fetch API provides a modern interface for making HTTP requests. It returns Promises and is built into modern browsers.

## Basic GET Request

```js
fetch("https://api.example.com/data")
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```

### With async/await

```js
async function getData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    return data;
  } catch (error) {
    console.error("Error:", error);
  }
}
```

## Response Object

```js
const response = await fetch(url);

console.log(response.ok); // true if status 200-299
console.log(response.status); // 200, 404, 500, etc.
console.log(response.statusText); // "OK", "Not Found"
console.log(response.headers); // Headers object
console.log(response.url); // Final URL after redirects
```

## Reading Response Body

```js
const response = await fetch(url);

// As JSON
const json = await response.json();

// As text
const text = await response.text();

// As Blob
const blob = await response.blob();

// As ArrayBuffer
const buffer = await response.arrayBuffer();

// As FormData
const formData = await response.formData();
```

**Note**: Body can only be read ONCE!

## POST Request

```js
const data = { name: "John", age: 30 };

const response = await fetch("https://api.example.com/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(data),
});

const result = await response.json();
```

## Request Options

```js
fetch(url, {
  method: "POST", // GET, POST, PUT, DELETE, PATCH
  headers: {
    "Content-Type": "application/json",
    Authorization: "Bearer token123",
  },
  body: JSON.stringify(data), // Request body
  mode: "cors", // cors, no-cors, same-origin
  credentials: "include", // include, same-origin, omit
  cache: "no-cache", // default, no-cache, reload, force-cache
  redirect: "follow", // follow, error, manual
});
```

## HTTP Methods

### GET

```js
const response = await fetch("/api/users");
```

### POST

```js
const response = await fetch("/api/users", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "John" }),
});
```

### PUT

```js
const response = await fetch("/api/users/1", {
  method: "PUT",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({ name: "Jane" }),
});
```

### DELETE

```js
const response = await fetch("/api/users/1", {
  method: "DELETE",
});
```

## Error Handling

**Important**: fetch only rejects on network errors, NOT HTTP errors!

```js
async function fetchData(url) {
  try {
    const response = await fetch(url);

    // Check for HTTP errors
    if (!response.ok) {
      throw new Error(`HTTP ${response.status}: ${response.statusText}`);
    }

    return await response.json();
  } catch (error) {
    if (error.name === "TypeError") {
      console.error("Network error:", error);
    } else {
      console.error("Request failed:", error);
    }
    throw error;
  }
}
```

## Sending Form Data

```js
const formData = new FormData();
formData.append("name", "John");
formData.append("file", fileInput.files[0]);

const response = await fetch("/api/upload", {
  method: "POST",
  body: formData, // No Content-Type header needed!
});
```

## URL Parameters

```js
const params = new URLSearchParams({
  search: "javascript",
  page: 1,
  limit: 10,
});

const response = await fetch(`/api/search?${params}`);
// /api/search?search=javascript&page=1&limit=10
```

## Headers

```js
// Create headers
const headers = new Headers();
headers.append("Content-Type", "application/json");
headers.append("Authorization", "Bearer token");

// Check headers
headers.has("Content-Type"); // true
headers.get("Authorization"); // 'Bearer token'

// Use in fetch
fetch(url, { headers });
```

## Abort Request

```js
const controller = new AbortController();
const { signal } = controller;

// Start request
fetch(url, { signal })
  .then((response) => response.json())
  .catch((error) => {
    if (error.name === "AbortError") {
      console.log("Request aborted");
    }
  });

// Abort after 5 seconds
setTimeout(() => controller.abort(), 5000);
```

## Timeout Pattern

```js
async function fetchWithTimeout(url, timeout = 5000) {
  const controller = new AbortController();
  const id = setTimeout(() => controller.abort(), timeout);

  try {
    const response = await fetch(url, { signal: controller.signal });
    clearTimeout(id);
    return response;
  } catch (error) {
    clearTimeout(id);
    throw error;
  }
}
```

## Common Patterns

### Reusable API Client

```js
const api = {
  baseUrl: "https://api.example.com",

  async request(endpoint, options = {}) {
    const response = await fetch(`${this.baseUrl}${endpoint}`, {
      headers: { "Content-Type": "application/json" },
      ...options,
    });
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    return response.json();
  },

  get(endpoint) {
    return this.request(endpoint);
  },
  post(endpoint, data) {
    return this.request(endpoint, {
      method: "POST",
      body: JSON.stringify(data),
    });
  },
};
```

## Key Points

> fetch returns a Promise

> Check response.ok for HTTP errors

> Body can only be read once

> Network errors reject, HTTP errors don't

> Use AbortController for cancellation

## Links

- [MDN Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
