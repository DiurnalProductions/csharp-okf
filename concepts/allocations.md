---
id: csharp.allocations
type: concept
title: Allocations and GC Pressure
description: How object creation drives garbage collection cost and latency.
tags: ['csharp', 'memory', 'performance']
prerequisites:
  - csharp.stack_vs_heap
  - csharp.garbage_collection
related:
  - csharp.span
  - csharp.boxing_and_unboxing
  - csharp.closures
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Each heap allocation contributes to GC work. Reducing allocations improves throughput and tail latency.

## Mental model

Allocations are cheap individually but add up in hot paths—LINQ chains, string concatenation in loops, boxing, closure captures, and async state machines all allocate. Object pooling (`ArrayPool<T>`) reuses buffers. Structs and `Span` avoid heap churn. Profile with dotMemory, PerfView, or `dotnet-gcdump`. Gen0 collections are frequent; surviving objects promote. LOH allocations are expensive and less compacted. Measure before micro-optimizing.

## Example

```csharp
// Prefer:
var sb = new StringBuilder();
foreach (var s in parts) sb.Append(s);
var result = sb.ToString();

// Over:
string result = "";
foreach (var s in parts) result += s; // many allocations
```

## Common mistakes

- Premature optimization without profiling evidence.
- Using `ArrayPool` and returning arrays still in use.
- Ignoring allocations from logging and exception construction in tight loops.

## Related concepts

- [csharp.span](/concepts/span.md)
- [csharp.boxing_and_unboxing](/concepts/boxing_and_unboxing.md)
- [csharp.closures](/concepts/closures.md)
