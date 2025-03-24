---
context:
  - "[[Bundler]]"
---

# esbuild

Extremely fast and efficient [[Bundler]] for [[Web Development]].

---

**Performance**: Written in Go (compiled to native code). Uses parallel processing and aggressive optimization techniques.

**File Types**: Supports multiple file types, including:
- [[JavaScript]] ([[ECMAScript|ES6+]], CommonJS)
- [[TypeScript]]
- JSX/TSX
- [[CSS]]
- [[JSON]]
- Images (as data URLs)

## Example

Converting a TypeScript file into a minified JavaScript file:

```bash
esbuild something.ts --bundle --minify --outfile=out.js
```
