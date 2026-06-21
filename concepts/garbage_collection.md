---
id: csharp.garbage_collection
type: concept
title: Garbage Collection
description: Automatic reclamation of unreachable managed objects by the CLR.
tags: ['csharp', 'runtime', 'gc', 'memory']
prerequisites:
  - csharp.clr
  - csharp.memory_management
related:
  - csharp.allocations
  - csharp.memory_management
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

The generational GC traces references from roots and compacts/reclaims unreachable objects, introducing pause times.

## Mental model

Most objects die young—gen0 collections are frequent and fast. Survivors promote to gen1/gen2. Full GCs are expensive. The GC is non-deterministic: you cannot predict when an object is collected. `GC.Collect()` is almost always wrong in application code. Finalization runs on a separate thread and prolongs object lifetime. Weak references allow caches without preventing collection. Server GC vs workstation GC tune threading for throughput vs latency.

## Example

```csharp
var weak = new WeakReference(new byte[10_000]);
// After strong refs gone and GC runs, weak.Target may be null
```

## Common mistakes

- Calling `GC.Collect()` routinely to 'help' the GC.
- Implementing finalizers without `Dispose` pattern.
- Creating memory leaks via static event handlers holding object graphs alive.

## Related concepts

- [csharp.allocations](/concepts/allocations.md)
- [csharp.memory_management](/concepts/memory_management.md)
