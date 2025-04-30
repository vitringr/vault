---
context:
  - "[[JavaScript]]"
---

# JavaScript Fetch API

The Fetch API provides an interface for making [[HTTP]] requests in JavaScript.

---

Provides a clean and flexible way to fetch resources [[JavaScript Async|asynchronously]].

**Modern**: Replaces the older `XMLHttpRequest` method.

```javascript
fetch(url, options)
  .then((response) => response.json())
  .then((data) => console.log(data))
  .catch((error) => console.error("Error:", error));
```
