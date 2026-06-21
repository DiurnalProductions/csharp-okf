---
id: csharp.closures
type: concept
title: Closures
description: Lambdas and local functions that capture variables from enclosing scopes.
tags: ['csharp', 'fundamentals', 'lambdas', 'memory']
prerequisites:
  - csharp.lambdas
related:
  - csharp.lambdas
  - csharp.delegates
  - csharp.allocations
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Captured variables live in compiler-generated closure objects on the heap, extending their lifetime.

## Mental model

When a lambda references `x` from an outer scope, the compiler hoists `x` into a hidden class field so the delegate can outlive the stack frame. Multiple lambdas may share one closure instance. This is why a loop-created lambda that captures the iterator variable can surprise you if semantics change. `static` lambdas forbid capturing locals/`this`. Closures are the bridge between functional syntax and CLR object semantics.

## Example

```csharp
Func<int> MakeCounter()
{
    int count = 0;
    return () => ++count; // captures count on heap
}
```

## Common mistakes

- Unintentionally capturing large state in long-lived delegates.
- Expecting captured variables to remain on the stack.
- Creating many closure instances in tight loops.

## Related concepts

- [csharp.lambdas](/concepts/lambdas.md)
- [csharp.delegates](/concepts/delegates.md)
- [csharp.allocations](/concepts/allocations.md)
