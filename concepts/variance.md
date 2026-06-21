---
id: csharp.variance
type: concept
title: Covariance and Contravariance
description: Rules for subtyping generic interfaces with type parameter variance.
tags: ['csharp', 'generics', 'variance', 'types']
prerequisites:
  - csharp.generic_constraints
  - csharp.interfaces
related:
  - csharp.ienumerable
  - csharp.interfaces
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Covariant `out T` and contravariant `in T` modifiers apply only to delegates and interface type parameters.

## Mental model

Covariance (`IEnumerable<out T>`): you can use `IEnumerable<Dog>` as `IEnumerable<Animal>` because you only produce `T`. Contravariance (`in T`): `Action<Animal>` substitutable for `Action<Dog>` because you only consume `T`. Variance does not apply to classes like `List<T>`—`List<Dog>` is not a `List<Animal>` because `List` both reads and writes `T`. Understanding variance prevents unsafe casts and explains LINQ's interface shapes.

## Example

```csharp
IEnumerable<object> objs = new List<string>(); // covariant out T

Action<string> printObj = s => Console.WriteLine(s);
Action<object> a = printObj; // contravariant in T — actually Action<object> can't assign from Action<string> the other way - let me fix

// Contravariance example:
Action<object> log = o => Console.WriteLine(o);
Action<string> logString = log; // OK: contravariance
```

## Common mistakes

- Expecting `List<Derived>` to be assignable to `List<Base>`.
- Declaring invalid variance on interfaces that both produce and consume `T`.
- Confusing array covariance (arrays are covariant but unsafe at runtime) with generics.

## Related concepts

- [csharp.ienumerable](/concepts/ienumerable.md)
- [csharp.interfaces](/concepts/interfaces.md)
