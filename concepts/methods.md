---
id: csharp.methods
type: concept
title: Methods
description: Named units of behavior with parameters, return types, and access modifiers.
tags: ['csharp', 'fundamentals', 'methods']
prerequisites:
  - csharp.variables
  - csharp.type_system
related:
  - csharp.overload_resolution
  - csharp.delegates
  - csharp.exceptions
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Methods encapsulate executable logic. Instance methods receive `this`; static methods belong to the type.

## Mental model

A method call compiles to `call`/`callvirt` IL. Virtual methods use dispatch through the object's method table. Parameters are passed by value by default—even reference types pass the reference by value (copy of the pointer). `ref`/`out`/`in` modify passing conventions. `async` methods return `Task` and are rewritten to state machines. Local functions capture outer variables like lambdas. Expression-bodied members are syntax sugar for simple returns.

## Example

```csharp
public static int Add(int a, int b) => a + b;

public void Swap(ref int x, ref int y) =>
    (x, y) = (y, x);
```

## Common mistakes

- Expecting `ref` on a reference type to allow reassigning the caller's variable without `ref`.
- Using `async void` except for event handlers.
- Returning mutable static state from methods.

## Related concepts

- [csharp.overload_resolution](/concepts/overload_resolution.md)
- [csharp.delegates](/concepts/delegates.md)
- [csharp.exceptions](/concepts/exceptions.md)
