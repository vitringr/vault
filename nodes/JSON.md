---
aliases:
  - JavaScript Object Notation
context:
  - "[[Data Format]]"
---

# JSON

(JavaScript Object Notation)

Standard, lightweight, text-based data-interchange format.

Based on [[JavaScript]] object syntax.

---

Stores data objects consisting of attribute-value pairs and arrays.

JSON files use the `.json` extension.

Example:

```json
{
  "first_name": "John",
  "last_name": "Smith",
  "is_alive": true,
  "age": 27,
  "address": {
    "street_address": "21 2nd Street",
    "city": "New York",
    "state": "NY",
    "postal_code": "10021-3100"
  },
  "phone_numbers": [
    {
      "type": "home",
      "number": "212 555-1234"
    },
    {
      "type": "office",
      "number": "646 555-4567"
    }
  ],
  "children": [
    "Catherine",
    "Thomas",
    "Trevor"
  ],
  "spouse": null
}
```
