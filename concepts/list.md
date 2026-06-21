---
id: csharp.list
type: concept
title: List<T>
description: Dynamic array-backed resizable list with indexed access.
tags: ['csharp', 'collections', 'list']
prerequisites:
  - csharp.ienumerable
related:
  - csharp.dictionary
  - csharp.arrays
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`List<T>` grows an internal array, amortized O(1) append, O(n) insert/remove in middle.

## Mental model

Capacity doubles when full—copies elements to new backing array. Indexer is O(1). Not thread-safe. `List<T>` is invariant—no covariance. Methods like `AddRange` may use `Span` internally in modern BCL. Prefer `List<T>` over `ArrayList` (non-generic, boxes value types). For read-heavy sharing, expose `IReadOnlyList<T>`.

## Example

```csharp
var items = new List<string> { "a", "b" };
items.Add("c");
items.Insert(0, "z");
```

## Common mistakes

- Removing items while iterating forward without index adjustment.
- Assuming `Count` equals `Capacity` (internal buffer may be larger).
- Using `List<T>` as default public API type instead of `IReadOnlyList<T>`.

## Related concepts

- [csharp.dictionary](/concepts/dictionary.md)
- [csharp.arrays](/concepts/arrays.md)
