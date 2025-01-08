---
context:
  - "[[JavaScript]]"
  - "[[Data Type (Computer Science)]]"
---

# JavaScript Data Type

The kind of data a [[JavaScript Variable]] can hold.

---

## Primitive Types

JavaScript has 7 [[Primitive Data Type|Primitive Data Types]]:

- **String**: Holds a sequence of characters. Represents text.
- **Number**: Represents numerical values.
- **BigInt**: Holds large integers of arbitrary size.
- **Boolean**: Represents `true` or `false` values.
- **Undefined**: Variables that are declared but not initialized.
- **Null**: Signifies deliberate absense of any object value.
- **Symbol**: Represents unique, immutable identifiers.

## Object

An [[Object (Computer Science)|Object]] in JavaScript is a non-primitive data type storing collections of key-value pairs.

Keys are strings (or symbols), and values can be any data type, including other objects.

Objects are mutable and are accessed by reference.

### Built-in Object

There are also a number of "global objects" that are built into the language specification itself.

Some examples are: _Number_, _Math_, _Date_, _String_, _Error_, _Function_, _Boolean_ ...

## The `typeof` Operator

The `typeof` operator returns a string indicating the type of the operand's value.
