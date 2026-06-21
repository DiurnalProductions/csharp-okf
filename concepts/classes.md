---
id: csharp.classes
type: concept
title: Classes
description: Reference types that define fields, properties, methods, and object identity.
tags: ['csharp', 'oop', 'classes']
prerequisites:
  - csharp.methods
  - csharp.value_types_vs_reference_types
related:
  - csharp.inheritance
  - csharp.interfaces
  - csharp.encapsulation
  - csharp.records
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Classes are heap-allocated reference types with identity equality by default and support inheritance.

## Mental model

A `new` expression allocates an object, runs field initializers, then the constructor chain. Reference equality means two distinct instances with identical data are not equal unless `Equals` is overridden. Virtual methods enable polymorphism. Properties are syntactic sugar over getter/setter methods. Partial classes split definition across files. `record class` adds value-based equality while remaining a reference type.

## Example

```csharp
public class Account
{
    public string Owner { get; init; } = "";
    public decimal Balance { get; private set; }
    public void Deposit(decimal amount) => Balance += amount;
}
```

## Common mistakes

- Implementing `==` without consistent `Equals` and `GetHashCode`.
- Exposing mutable collections without defensive copies.
- Using classes for small immutable data where `struct` or `record struct` would reduce allocations.

## Related concepts

- [csharp.inheritance](/concepts/inheritance.md)
- [csharp.interfaces](/concepts/interfaces.md)
- [csharp.encapsulation](/concepts/encapsulation.md)
- [csharp.records](/concepts/records.md)
