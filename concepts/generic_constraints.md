---
id: csharp.generic_constraints
type: concept
title: Generic Constraints
description: Bounds on type parameters specifying required capabilities.
tags: ['csharp', 'generics', 'constraints']
prerequisites:
  - csharp.generic_classes
related:
  - csharp.variance
  - csharp.generic_methods
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Constraints (`where T : class`, `struct`, `new()`, base type, interface) enable safe operations on `T`.

## Mental model

Constraints are validated at compile time for each closed instantiation. `where T : struct` excludes null for unconstrained nullable value handling. `where T : class?` allows nullable reference type parameters. `unmanaged` enables pointer operations. Combining constraints narrows the set of permissible types. The compiler emits calls against constraint surfaces—interface calls may still box value types unless optimized via generics specialization.

## Example

```csharp
public static T Create<T>() where T : new()
    => new T();

public static int Compare<T>(T a, T b) where T : IComparable<T>
    => a.CompareTo(b);
```

## Common mistakes

- Over-constraining `T` when a non-generic overload would suffice.
- Using `class` constraint when `notnull` or specific interface is needed.
- Forgetting `struct` constraint disallows nullable value type parameters without `T?` handling.

## Related concepts

- [csharp.variance](/concepts/variance.md)
- [csharp.generic_methods](/concepts/generic_methods.md)
