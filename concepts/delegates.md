---
id: csharp.delegates
type: concept
title: Delegates
description: Type-safe function pointers that underpin events, callbacks, and lambdas.
tags: ['csharp', 'fundamentals', 'delegates', 'functional']
prerequisites:
  - csharp.methods
related:
  - csharp.lambdas
  - csharp.task
  - csharp.closures
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Delegates are reference types wrapping method references. Multicast delegates invoke multiple targets in order.

## Mental model

A delegate instance is a heap object holding a list of (object, method pointer) pairs. `Func<T>` and `Action` are BCL delegate types. Invocation is synchronous unless you wrap it yourself. Events are delegates with add/remove accessors restricting invocation. The compiler generates closure classes when lambdas capture locals. Understanding delegates explains how LINQ passes predicates and how `Task` continuations are scheduled.

## Example

```csharp
Func<int, bool> isEven = n => n % 2 == 0;
var nums = new[] { 1, 2, 3 }.Where(isEven);
```

## Common mistakes

- Forgetting to unsubscribe from events, causing leaks.
- Assuming delegate invocation order is guaranteed across `-=` removals.
- Comparing delegates by method only, ignoring target object.

## Related concepts

- [csharp.lambdas](/concepts/lambdas.md)
- [csharp.task](/concepts/task.md)
- [csharp.closures](/concepts/closures.md)
