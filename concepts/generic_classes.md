---
id: csharp.generic_classes
type: concept
title: Generic Classes
description: Types parameterized by type arguments, reified at runtime in .NET.
tags: ['csharp', 'generics', 'types']
prerequisites:
  - csharp.type_system
related:
  - csharp.generic_methods
  - csharp.generic_constraints
  - csharp.list
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Generic classes like `List<T>` are defined with type parameters instantiated into closed constructed types at runtime.

## Mental model

Unlike Java's type erasure, .NET generics are reified: `List<int>` and `List<string>` are distinct runtime types with specialized code paths where JIT creates them. Type parameters can be value or reference types—no boxing for `T` when `T` is `int`. Open generic types (`List<>`) cannot be instantiated directly. Generic static fields are per closed type. This reification enables constraints, reflection on `T`, and performance without casts.

## Example

```csharp
public class Box<T>
{
    public T Value { get; set; }
    public Box(T value) => Value = value;
}

var n = new Box<int>(42);
var s = new Box<string>("ok");
```

## Common mistakes

- Assuming one static field shared across all `T` (it's per closed type).
- Storing `T` as `object` unnecessarily, causing boxing for value types.
- Creating overly generic types when a non-generic design is clearer.

## Related concepts

- [csharp.generic_methods](/concepts/generic_methods.md)
- [csharp.generic_constraints](/concepts/generic_constraints.md)
- [csharp.list](/concepts/list.md)
