---
id: csharp.stack_vs_heap
type: concept
title: Stack vs Heap
description: Where locals and objects live in the managed execution model.
tags: ['csharp', 'memory', 'performance']
prerequisites:
  - csharp.value_types_vs_reference_types
related:
  - csharp.memory_management
  - csharp.allocations
  - csharp.span
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Stack frames hold value-type locals and return addresses; heap holds reference type objects and boxed values.

## Mental model

Each thread has a stack growing with method calls. Value type locals live in the stack frame (unless escaped via boxing, async state machine fields, or closure capture). `new` allocates on the managed heap. Escaping analysis: if a reference to stack memory could outlive the frame, the compiler boxes or moves data to the heap. `ref struct` types cannot escape to the heap. Understanding this explains performance differences and struct sizing guidance.

## Example

```csharp
int local = 42;           // stack
var sb = new StringBuilder(); // object on heap, reference on stack
Span<int> span = stackalloc int[16]; // stack buffer
```

## Common mistakes

- Claiming all structs are always on the stack (instance fields live with objects).
- Returning ref to local variable (illegal and unsafe if attempted).
- Ignoring heap pressure from many short-lived objects.

## Related concepts

- [csharp.memory_management](/concepts/memory_management.md)
- [csharp.allocations](/concepts/allocations.md)
- [csharp.span](/concepts/span.md)
