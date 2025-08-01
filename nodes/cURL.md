---
aliases:
  - curl
context:
  - "[[Software Application]]"
---

# cURL

[[CLI Application]] for transferring data over networks.

---

Lightweight, universal and powerful.

Uses various network protocols.

```bash
curl options URL
```

## Common Commands

Basic requests:

| Command                                  | Description                               |
| ---------------------------------------- | ----------------------------------------- |
| `curl https://example.com`               | Fetch a webpage                           |
| `curl -o output.txt https://example.com` | Save response to a file                   |
| `curl -O https://example.com/file.zip`   | Download a file (keeps original filename) |

[[HTTP]] methods:

| Command                                       | Description                    |
| --------------------------------------------- | ------------------------------ |
| `curl -X GET https://api.example.com/data`    | Explicit GET request (default) |
| `curl -X POST https://api.example.com/data`   | Send a POST request            |
| `curl -X PUT https://api.example.com/data`    | Send a PUT request             |
| `curl -X DELETE https://api.example.com/data` | Send a DELETE request          |

Sending data:

| Command                                                                                 | Description           |
| --------------------------------------------------------------------------------------- | --------------------- |
| `curl -d "name=John&age=30" https://api.example.com`                                    | Send form data (POST) |
| `curl -d '{"key":"value"}' -H "Content-Type: application/json" https://api.example.com` | Send JSON data        |
| `curl -F "file=@photo.jpg" https://api.example.com/upload`                              | Upload a file         |
