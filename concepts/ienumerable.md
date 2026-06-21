---
id: csharp.ienumerable
type: concept
title: IEnumerable and Iteration
description: The foundational sequence abstraction enabling foreach and LINQ.
tags: ['csharp', 'collections', 'linq', 'iteration']
prerequisites:
  - csharp.arrays
  - csharp.generic_classes
related:
  - csharp.linq
  - csharp.deferred_execution
  - csharp.variance
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`IEnumerable<T>` exposes an enumerator for sequential access. `foreach` desugars to enumerator pattern or pattern-based iteration.

## Mental model

Enumeration is pull-based: `MoveNext` advances, `Current` yields item. Multiple enumeration restarts from a fresh enumerator unless the source is single-pass (e.g., lazy LINQ or streaming). `IAsyncEnumerable<T>` extends the model for async streams. Compiler lowers `foreach` to try/finally disposing `IDisposable` enumerators. Custom types implement `GetEnumerator` or extension `GetAsyncEnumerator`.

## Example

```csharp
foreach (var item in collection)
    Console.WriteLine(item);

// Equivalent pattern:
using var e = collection.GetEnumerator();
while (e.MoveNext())
    Console.WriteLine(e.Current);
```

## Common mistakes

- Enumerating `IEnumerable` multiple times when LINQ pipeline is single-use.
- Modifying a collection during foreach without invalidation handling.
- Confusing `IEnumerable` (deferred) with materialized collections.

## Related concepts

- [csharp.linq](/concepts/linq.md)
- [csharp.deferred_execution](/concepts/deferred_execution.md)
- [csharp.variance](/concepts/variance.md)
