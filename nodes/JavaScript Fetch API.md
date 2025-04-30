---
context:
  - "[[JavaScript]]"
---

# JavaScript Fetch API

The Fetch API provides an interface for making [[HTTP]] requests in JavaScript.

---

Provides a clean and flexible way to fetch resources [[JavaScript Async|asynchronously]].

**Modern**: Replaces the older `XMLHttpRequest` method.

## Usage

Use the global `fetch()` method.

Basic Usage:

```javascript
fetch(url, options)
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```

POST Request with [[JSON]]:

```javascript
fetch("https://api.example.com/data", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    key: "value",
    anotherKey: "anotherValue",
  }),
})
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```
