---
aliases:
  - Linear Space
context:
  - "[[Linear Algebra]]"
---

# Vector Space

(Linear Space)

Defines a context of rules for [[Vector|Vectors]] and their operations.

---

_This is the formal mathematical 'universe' of vectors._

A vector space is a set of elements (called vectors) that can be added together and multiplied by [[Scalar|scalars]], satisfying certain axioms.

**Basis Vectors**: The vector space is characterized by a set of [[Basis Vectors]] that define a [[Coordinate System]] for it.

## Abstraction

The generalization of vector space enables abstraction where many things can be treated as vectors as long as they obey these axioms.

**Consistency**: The ruleset of axioms guarantees that all the familiar vector operations will work consistently and predictably between abstractions.

## Axioms

For any vectors `u`, `v`, `w` in the space, and any scalars `a`, `b`, the following must always hold:

**Closure Under Addition**: For any `u` and `v` in the space, `u + v` is also in the space.

**Closure Under Scalar Multiplication**: For any `u` in the space, `a * u` is also in the space.

**Commutativity of Addition**: For any `u` and `v`, `u + v = v + u`.

**Associativity of Addition**: For any `u`, `v`, and `w`, `(u + v) + w = u + (v + w)`.

**Additive Identity**: For any `v`, there exists a zero vector `0` such that `v + 0 = v`.

**Additive Inverse**: For any `v`, there exists a vector `-v` such that `v + (-v) = 0`.

**Multiplicative Identity**: For any `x`, there exist a scalar such that `1x = x`.

**Associativity of Scalar Multiplication**: For any `x`, and for any scalars `a` and `b`, `(ab)x = a(bx)`.

**Distribution of Elements to Scalars**: For any `x` and `y`, and any scalar `a`, `a(x + y) = ax + ay`.

**Distribution of Scalars to Elements**: For any `x`, and any scalars `a` and `b`, `(a + b)x = ax + bx`.
