---
id: csharp.deferred_execution
type: concept
title: Deferred Execution
description: LINQ operators that delay work until enumeration occurs.
tags: ['csharp', 'linq', 'performance', 'iteration']
prerequisites:
  - csharp.linq
  - csharp.ienumerable
related:
  - csharp.linq
  - csharp.allocations
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Most LINQ operators build iterator graphs; execution happens on `foreach`, `ToList`, etc.

## Mental model

Deferred operators capture source and predicates without running them. Side effects in lambdas run at enumeration time, not at pipeline construction. Terminal operators (`Count`, `ToArray`, `First`) force execution. Chaining deferred operators is cheap; repeating enumeration may repeat work. Use `ToList`/`ToArray` when you need stable snapshots or multiple passes. This model mirrors database query planning—build plan, execute later.

## Example

```csharp
var query = source.Where(x => { Log(x); return x > 0; });
// Log not called yet
foreach (var x in query) { } // now Log runs per element
```

## Common mistakes

- Closing/disposing source before deferred query executes.
- Multiple enumerations of expensive pipelines without caching.
- Expecting exceptions from deferred operators at pipeline build time.

## Related concepts

- [csharp.linq](/concepts/linq.md)
- [csharp.allocations](/concepts/allocations.md)
