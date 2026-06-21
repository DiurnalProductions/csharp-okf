---
id: csharp.interfaces
type: concept
title: Interfaces
description: Contracts defining members that implementing types must provide.
tags: ['csharp', 'oop', 'interfaces']
prerequisites:
  - csharp.classes
related:
  - csharp.inheritance
  - csharp.polymorphism
  - csharp.variance
  - csharp.dependency_injection
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Interfaces enable polymorphism without implementation inheritance. Types can implement multiple interfaces.

## Mental model

Interface calls may be dispatch via virtual stub or constrained generic calls without boxing. Default interface methods (C# 8+) add implementation to interfaces but complicate diamond scenarios. Explicit implementation hides members from casual callers. Interfaces are reference types at runtime when used as constraints or variables—structs box when cast to interface unless generic constrained call avoids it. DI containers bind interfaces to implementations at composition root.

## Example

```csharp
public interface IRepository<T>
{
    Task<T?> FindAsync(Guid id, CancellationToken ct = default);
}

public class InMemoryRepo<T> : IRepository<T> { /* ... */ }
```

## Common mistakes

- Fat interfaces violating interface segregation.
- Casting aggressively instead of depending on abstractions.
- Ignoring that default interface methods are not inherited like class virtual methods.

## Related concepts

- [csharp.inheritance](/concepts/inheritance.md)
- [csharp.polymorphism](/concepts/polymorphism.md)
- [csharp.variance](/concepts/variance.md)
- [csharp.dependency_injection](/concepts/dependency_injection.md)
