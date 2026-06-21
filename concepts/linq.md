---
id: csharp.linq
type: concept
title: LINQ Mental Model
description: Language-Integrated Query as composable sequence operators over IEnumerable.
tags: ['csharp', 'linq', 'collections', 'functional']
prerequisites:
  - csharp.ienumerable
  - csharp.lambdas
related:
  - csharp.deferred_execution
  - csharp.deferred_execution
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

LINQ is a query abstraction—method syntax and query syntax compile to operator chains, often lazily evaluated.

## Mental model

LINQ is not merely syntax sugar—it encodes a query algebra: map (`Select`), filter (`Where`), fold (`Aggregate`), etc. Query syntax desugars to method calls. Operators return new iterator objects holding delegates and upstream sequences. Understanding LINQ as deferred pipelines explains side effects order and multiple enumeration costs. `IQueryable` extends the model to expression trees for remote providers (EF Core).

## Example

```csharp
var result = people
    .Where(p => p.Age >= 18)
    .OrderBy(p => p.Name)
    .Select(p => p.Name);

// query syntax equivalent:
var q = from p in people
        where p.Age >= 18
        orderby p.Name
        select p.Name;
```

## Common mistakes

- Materializing too early with `ToList` before composing filters.
- Assuming query syntax is more efficient than method syntax (they are equivalent).
- Using LINQ where simple loops would be clearer and faster.

## Related concepts

- [csharp.deferred_execution](/concepts/deferred_execution.md)
- [csharp.deferred_execution](/concepts/deferred_execution.md)
