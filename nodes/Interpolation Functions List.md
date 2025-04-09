---
tags:
  - "data"
aliases:
  - Easing Functions List
context:
  - "[[Interpolation Function]]"
---

# Interpolation Functions List

Collection of useful interpolation functions:

```typescript
function linear(step: number) {
  return step;
}

// Quadratic
function easeInQuad(step: number) {
  return step * step;
}

function easeOutQuad(step: number) {
  return step * (2 - step);
}

function easeInOutQuad(step: number) {
  return step < 0.5 ? 2 * step * step : -1 + (4 - 2 * step) * step;
}

// Cubic
function easeInCubic(step: number) {
  return step * step * step;
}

function easeOutCubic(step: number) {
  return --step * step * step + 1;
}

function easeInOutCubic(step: number) {
  return step < 0.5
    ? 4 * step * step * step
    : (step - 1) * (2 * step - 2) * (2 * step - 2) + 1;
}

// Quartic
function easeInQuart(step: number) {
  return step * step * step * step;
}

function easeOutQuart(step: number) {
  return 1 - --step * step * step * step;
}

function easeInOutQuart(step: number) {
  return step < 0.5
    ? 8 * step * step * step * step
    : 1 - 8 * --step * step * step * step;
}

// Quintic
function easeInQuint(step: number) {
  return step * step * step * step * step;
}

function easeOutQuint(step: number) {
  return 1 + --step * step * step * step * step;
}

function easeInOutQuint(step: number) {
  return step < 0.5
    ? 16 * step * step * step * step * step
    : 1 + 16 * --step * step * step * step * step;
}

// Sine
function easeInSine(step: number) {
  return 1 - Math.cos((step * Math.PI) / 2);
}

function easeOutSine(step: number) {
  return Math.sin((step * Math.PI) / 2);
}

function easeInOutSine(step: number) {
  return -(Math.cos(Math.PI * step) - 1) / 2;
}

// Exponential
function easeInExpo(step: number) {
  return step === 0 ? 0 : Math.pow(2, 10 * (step - 1));
}

function easeOutExpo(step: number) {
  return step === 1 ? 1 : 1 - Math.pow(2, -10 * step);
}

function easeInOutExpo(step: number) {
  if (step === 0) return 0;
  if (step === 1) return 1;
  return step < 0.5
    ? Math.pow(2, 20 * step - 10) / 2
    : (2 - Math.pow(2, -20 * step + 10)) / 2;
}

// Circular
function easeInCirc(step: number) {
  return 1 - Math.sqrt(1 - step * step);
}

function easeOutCirc(step: number) {
  return Math.sqrt(1 - --step * step);
}

function easeInOutCirc(step: number) {
  return step < 0.5
    ? (1 - Math.sqrt(1 - 4 * step * step)) / 2
    : (Math.sqrt(1 - (-2 * step + 2) * (-2 * step + 2)) + 1) / 2;
}

// Back
function easeInBack(step: number) {
  const c1 = 1.70158;
  return step * step * ((c1 + 1) * step - c1);
}

function easeOutBack(step: number) {
  const c1 = 1.70158;
  return 1 + --step * step * ((c1 + 1) * step + c1);
}

function easeInOutBack(step: number) {
  const c2 = 1.70158 * 1.525;
  return step < 0.5
    ? (4 * step * step * ((c2 + 1) * 2 * step - c2)) / 2
    : ((2 * step - 2) * (2 * step - 2) * ((c2 + 1) * (step * 2 - 2) + c2) + 2) /
        2;
}

// Elastic
function easeInElastic(step: number) {
  if (step === 0) return 0;
  if (step === 1) return 1;
  return (
    -Math.pow(2, 10 * step - 10) *
    Math.sin(((step * 10 - 10.75) * (2 * Math.PI)) / 3)
  );
}

function easeOutElastic(step: number) {
  if (step === 0) return 0;
  if (step === 1) return 1;
  return (
    Math.pow(2, -10 * step) *
      Math.sin(((step * 10 - 0.75) * (2 * Math.PI)) / 3) +
    1
  );
}

function easeInOutElastic(step: number) {
  if (step === 0) return 0;
  if (step === 1) return 1;
  return step < 0.5
    ? -(
        Math.pow(2, 20 * step - 10) *
        Math.sin(((20 * step - 11.125) * (2 * Math.PI)) / 4.5)
      ) / 2
    : (Math.pow(2, -20 * step + 10) *
        Math.sin(((20 * step - 11.125) * (2 * Math.PI)) / 4.5)) /
        2 +
        1;
}

// Bounce
function easeInBounce(step: number) {
  return 1 - easeOutBounce(1 - step);
}

function easeOutBounce(step: number) {
  if (step < 1 / 2.75) {
    return 7.5625 * step * step;
  } else if (step < 2 / 2.75) {
    return 7.5625 * (step -= 1.5 / 2.75) * step + 0.75;
  } else if (step < 2.5 / 2.75) {
    return 7.5625 * (step -= 2.25 / 2.75) * step + 0.9375;
  } else {
    return 7.5625 * (step -= 2.625 / 2.75) * step + 0.984375;
  }
}

function easeInOutBounce(step: number) {
  return step < 0.5
    ? (1 - easeOutBounce(1 - 2 * step)) / 2
    : (1 + easeOutBounce(2 * step - 1)) / 2;
}
```
