---
aliases:
  - Minification
context:
  - "[[Software]]"
  - "[[Build Automation]]"
---

# Minification (Software)

Compression of code files by reducing file sizes without affecting functionality.

---

- Comments are removed from the code.
- Names are replaced with shorted ones.
- Spaces, tabs, and newlines are removed.
- Optimizes syntax by reducing redundant code.
- Multiple files can be merged into one.

```javascript
// This is a comment that will be removed by the minifier

var array = [];

for (var i = 0; i < 20; i++) {
  array[i] = i;
}
```

to

```javascript
for(var a=[],i=0;i<20;a[i]=i++);
```
