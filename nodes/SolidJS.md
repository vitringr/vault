---
context:
  - "[[Software Framework]]"
  - "[[JavaScript]]"
---

# SolidJS

Solid is a declarative [[JavaScript]] framework for creating reactive and performant user interfaces.

---

See the [Website](https://www.solidjs.com) and [Documentation](https://docs.solidjs.com).

Solid embraces the [[Reactive Programming]] paradigm.

Full [[TypeScript]] integration, as it is written with it.

Designed to align closely with [[HTML]] standards, Solid uses [[JSX]] and [[TSX]].

```jsx
import { onCleanup, createSignal } from "solid-js";
import { render } from "solid-js/web";

const CountingComponent = () => {
  const [count, setCount] = createSignal(0);

  const interval = setInterval(() => setCount((count) => count + 1), 1000);

  onCleanup(() => clearInterval(interval));

  return <div>Count value is {count()}</div>;
};

render(() => <CountingComponent />, document.getElementById("app"));
```

