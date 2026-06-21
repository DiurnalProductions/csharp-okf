---
id: csharp.arrays
type: concept
title: Arrays
description: Fixed-length, zero-based indexed collections with rank and element type.
tags: ['csharp', 'collections', 'arrays']
prerequisites:
  - csharp.type_system
related:
  - csharp.ienumerable
  - csharp.span
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Arrays are reference types with contiguous memory layout, covariant for reference element types only.

## Mental model

One-dimensional arrays implement `IList<T>` and `T[]` with `Length` fixed at allocation. `int[]` is not covariant to `object[]` (value types). `string[]` is covariant to `object[]` but writing wrong element type throws `ArrayTypeMismatchException`. Multidimensional arrays (`[,]`) differ from jagged (`[][]`). `stackalloc` creates stack-backed spans for small buffers. Arrays are simple but lack grow semantics—`List<T>` wraps dynamic growth.

## Example

```csharp
int[] primes = { 2, 3, 5, 7 };
Span<int> slice = primes.AsSpan(1, 2); // { 3, 5 }
```

## Common mistakes

- Using arrays when `List<T>` or `Span<T>` fits better.
- Relying on reference array covariance for value types.
- Off-by-one errors with `Length` vs last index.

## Related concepts

- [csharp.ienumerable](/concepts/ienumerable.md)
- [csharp.span](/concepts/span.md)
