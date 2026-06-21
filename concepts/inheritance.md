---
id: csharp.inheritance
type: concept
title: Inheritance
description: Deriving classes from base classes to reuse and specialize behavior.
tags: ['csharp', 'oop', 'inheritance']
prerequisites:
  - csharp.classes
  - csharp.interfaces
related:
  - csharp.polymorphism
  - csharp.encapsulation
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

C# supports single class inheritance and multiple interface implementation. `sealed` prevents further derivation.

## Mental model

Derived constructors must chain to a base constructor. Virtual/override pairs enable substitutability. `new` keyword hides base members without polymorphism. Base class fields share one allocation with derived payload. Favor composition when behavior variation does not map to is-a relationships. Inheritance couples derived types to base implementation changes—fragile base class problem.

## Example

```csharp
public abstract class Shape
{
    public abstract double Area { get; }
}

public sealed class Circle : Shape
{
    public double Radius { get; }
    public Circle(double r) => Radius = r;
    public override double Area => Math.PI * Radius * Radius;
}
```

## Common mistakes

- Deep inheritance hierarchies instead of composition.
- Calling virtual methods from constructors (subclass not fully initialized).
- Using inheritance purely for code reuse without is-a semantics.

## Related concepts

- [csharp.polymorphism](/concepts/polymorphism.md)
- [csharp.encapsulation](/concepts/encapsulation.md)
