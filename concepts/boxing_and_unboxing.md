---
id: csharp.boxing_and_unboxing
type: concept
title: Boxing and Unboxing
description: Converting value types to reference types and back via heap allocation.
tags: ['csharp', 'fundamentals', 'memory', 'performance']
prerequisites:
  - csharp.value_types_vs_reference_types
related:
  - csharp.allocations
  - csharp.stack_vs_heap
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Boxing wraps a value type in a heap-allocated object; unboxing extracts the value with a cast.

## Mental model

When a value type is converted to `object` or an interface it implements, the CLR allocates a box on the heap, copies the value into it, and returns a reference. Unboxing retrieves that copy—it does not return a reference to interior storage. Each box is a separate allocation subject to GC. Boxing is invisible in source but shows up in profiles as allocation pressure. Generics that are reified avoid boxing for type parameters constrained to `struct` when used as `T` directly, but storing a struct as `object` always boxes.

## Example

```csharp
int i = 42;
object boxed = i;      // allocates box on heap
int j = (int)boxed;    // unbox — InvalidCastException if wrong type

IEnumerable<int> nums = new List<int> { 1 };
// No boxing when enumerating List<int>
```

## Common mistakes

- Boxing in hot loops via non-generic collections (`ArrayList`).
- Unboxing to the wrong type or after the box was mutated via a different path.
- Assuming `enum` stored as `object` avoids boxing (it does not).

## Related concepts

- [csharp.allocations](/concepts/allocations.md)
- [csharp.stack_vs_heap](/concepts/stack_vs_heap.md)
