---
id: csharp.span
type: concept
title: Span<T> and Memory<T>
description: Stack-safe, sliceable views over contiguous memory without heap allocation.
tags: ['csharp', 'memory', 'performance', 'span']
prerequisites:
  - csharp.arrays
  - csharp.stack_vs_heap
related:
  - csharp.allocations
  - csharp.value_semantics
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`Span<T>` is a ref struct slicing arrays, stack memory, or native buffers with bounds-checked access.

## Mental model

`Span<T>` cannot be stored on the heap—no fields in regular classes, no boxing, no async. `Memory<T>` is heap-friendly for async scenarios with `Span` via `.Span` synchronously. Slicing is O(1) copying span descriptor (pointer + length). APIs accepting `ReadOnlySpan<char>` reduce allocations in parsing. `stackalloc` + `Span` replaces small `byte[]` temporaries. Modern BCL methods overload for spans to avoid copies.

## Example

```csharp
ReadOnlySpan<char> text = "Hello, World".AsSpan();
var hello = text[..5];

Span<byte> buffer = stackalloc byte[256];
```

## Common mistakes

- Storing `Span<T>` in fields or async methods.
- Using `Memory<T>` without understanding pinning when interfacing with native code.
- Slicing without checking lengths leading to runtime exceptions.

## Related concepts

- [csharp.allocations](/concepts/allocations.md)
- [csharp.value_semantics](/concepts/value_semantics.md)
