---
id: csharp.generic_methods
type: concept
title: Generic Methods
description: Methods with their own type parameters, inferred or specified at call sites.
tags: ['csharp', 'generics', 'methods']
prerequisites:
  - csharp.generic_classes
related:
  - csharp.generic_constraints
  - csharp.linq
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Generic methods enable algorithms independent of specific types, with compile-time type inference.

## Mental model

Type inference examines argument types to solve type parameters: `Swap(ref a, ref b)` infers `T` from `a`. Failed inference yields compile errors. Generic methods can be declared on generic or non-generic types. Constraints limit allowable type arguments. Extension methods are static generic methods in static classes. LINQ's `Enumerable.Select` is a generic method chain building deferred pipelines.

## Example

```csharp
static void Swap<T>(ref T a, ref T b) => (a, b) = (b, a);

static T[] Of<T>(params T[] items) => items;

var nums = Of(1, 2, 3); // T inferred as int
```

## Common mistakes

- Specifying type arguments when inference is clearer (`Method<int>(...)` noise).
- Failing to constrain `T` when using operators or `new()`.
- Confusing method generic params with type generic params in nested scopes.

## Related concepts

- [csharp.generic_constraints](/concepts/generic_constraints.md)
- [csharp.linq](/concepts/linq.md)
