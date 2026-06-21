---
id: csharp.polymorphism
type: concept
title: Polymorphism
description: Operating on abstractions with runtime dispatch to concrete implementations.
tags: ['csharp', 'oop', 'polymorphism']
prerequisites:
  - csharp.inheritance
related:
  - csharp.interfaces
  - csharp.inheritance
  - csharp.methods
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Virtual methods and interface implementations let code treat specialized types uniformly through base references.

## Mental model

Polymorphism in C# is primarily subtype polymorphism: a `Shape` reference can point to a `Circle`, and `Area` dispatches to the override. Interface references work similarly. Pattern matching (C# 7+) adds structural polymorphism without inheritance. Generics with constraints provide compile-time polymorphism without virtual dispatch cost. Choose virtual dispatch for extensibility; generics for performance and type safety.

## Example

```csharp
void PrintAreas(IEnumerable<Shape> shapes)
{
    foreach (var s in shapes)
        Console.WriteLine(s.Area);
}
```

## Common mistakes

- Overusing `virtual` when sealing would clarify intent.
- Type-checking with `is`/`switch` when double dispatch or visitor would scale better.
- Assuming overload resolution is polymorphic (it is not—only virtual calls are).

## Related concepts

- [csharp.interfaces](/concepts/interfaces.md)
- [csharp.inheritance](/concepts/inheritance.md)
- [csharp.methods](/concepts/methods.md)
