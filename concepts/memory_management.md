---
id: csharp.memory_management
type: concept
title: Memory Management Fundamentals
description: How managed memory is allocated, tracked, and reclaimed in .NET.
tags: ['csharp', 'runtime', 'memory']
prerequisites:
  - csharp.clr
  - csharp.stack_vs_heap
related:
  - csharp.garbage_collection
  - csharp.allocations
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Managed code allocates reference types on the heap; the GC reclaims unreachable objects. Stack memory is automatic for value-type locals.

## Mental model

The CLR allocator carves objects from managed heaps (generational: gen0, gen1, gen2, LOH). References form a reachability graph from roots (stacks, statics, handles). No manual `free`—deterministic cleanup uses `IDisposable` / `using`. Large object allocations may trigger full collections. Understanding generations explains why short-lived allocations are cheap and why LOH fragmentation matters. `stackalloc` and `Span<T>` offer stack-backed buffers without GC pressure when used carefully.

## Example

```csharp
using var stream = File.OpenRead("data.bin");
// Dispose called at end of scope — deterministic cleanup of unmanaged handle
```

## Common mistakes

- Equating GC with instant memory reclamation.
- Not disposing types that wrap unmanaged resources.
- Holding references to large graphs longer than necessary.

## Related concepts

- [csharp.garbage_collection](/concepts/garbage_collection.md)
- [csharp.allocations](/concepts/allocations.md)
