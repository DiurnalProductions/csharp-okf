---
id: csharp.value_types_vs_reference_types
type: concept
title: Value Types vs Reference Types
description: The fundamental split in C# memory and assignment semantics.
tags: ['csharp', 'fundamentals', 'memory', 'types']
prerequisites:
  - csharp.type_system
related:
  - csharp.stack_vs_heap
  - csharp.boxing_and_unboxing
  - csharp.classes
  - csharp.structs
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Value types copy by value; reference types copy references. This distinction drives assignment, equality, mutability, and performance.

## Mental model

Value types (`struct`, primitives, enums) embed their payload wherever the variable lives—typically the stack for locals. Assignment copies the entire value bit-for-bit. Reference types (`class`, `interface`, `delegate`, `string`, arrays) store a reference (pointer) to a heap object; assignment copies only the reference, so two variables can alias the same object. `==` on reference types compares references by default (unless overloaded); value types compare fields unless overridden. This split is why mutating a struct through a copy does not affect the original, but mutating an object through a shared reference does.

## Example

```csharp
struct Point { public int X, Y; }
class Label { public string Text = ""; }

var p1 = new Point { X = 1 };
var p2 = p1;
p2.X = 9; // p1.X still 1

var a = new Label { Text = "hi" };
var b = a;
b.Text = "bye"; // a.Text is now "bye"
```

## Common mistakes

- Expecting reference-type assignment to clone the object.
- Mutating a struct copied from a dictionary or list without reassigning it back.
- Treating `string` as a value type in aliasing discussions—it is an immutable reference type.

## Related concepts

- [csharp.stack_vs_heap](/concepts/stack_vs_heap.md)
- [csharp.boxing_and_unboxing](/concepts/boxing_and_unboxing.md)
- [csharp.classes](/concepts/classes.md)
- [csharp.structs](/concepts/structs.md)
