---
id: csharp.clr
type: concept
title: Common Language Runtime (CLR)
description: The execution engine that loads assemblies, JIT-compiles IL, and manages memory.
tags: ['csharp', 'runtime', 'clr', 'dotnet']
prerequisites:
  - csharp.il
related:
  - csharp.garbage_collection
  - csharp.memory_management
  - csharp.assemblies
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

The CLR provides type system enforcement at runtime, JIT compilation, GC, exception handling, and threading primitives.

## Mental model

When you `dotnet run`, the CoreCLR host loads your assembly and dependencies, resolves types, JITs methods, and executes managed code. The CLR verifies IL (when applicable), enforces memory safety for managed pointers, schedules the GC, and propagates exceptions. Value types exist in IL with `unbox`/`box`; the runtime knows layout. Understanding CLR behavior explains why finalizers are non-deterministic, why static constructors run once per type, and why assembly load context matters.

## Example

```csharp
// Static constructor runs once per AppDomain / load context
class Cache
{
    static Cache() { /* initialize */ }
}
```

## Common mistakes

- Assuming `struct` on the stack always—locals yes, but fields live with their containing object.
- Relying on finalizers for timely resource cleanup.
- Ignoring assembly binding and load context in plugin scenarios.

## Related concepts

- [csharp.garbage_collection](/concepts/garbage_collection.md)
- [csharp.memory_management](/concepts/memory_management.md)
- [csharp.assemblies](/concepts/assemblies.md)
