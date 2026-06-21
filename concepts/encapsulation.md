---
id: csharp.encapsulation
type: concept
title: Encapsulation
description: Hiding internal state and exposing controlled operations through members.
tags: ['csharp', 'oop', 'encapsulation']
prerequisites:
  - csharp.classes
related:
  - csharp.classes
  - csharp.interfaces
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Access modifiers, properties, and immutability patterns protect invariants and reduce coupling.

## Mental model

Encapsulation is enforced at compile time via `private`, `protected`, `internal`, and `file` scopes. Properties decouple storage from API. `init` setters allow construction-time mutation only. `required` properties enforce object initializer completeness. Immutable objects simplify threading because shared state cannot change. Encapsulation is not secrecy—it is maintaining valid object states by constraining how data is read and written.

## Example

```csharp
public sealed class Temperature
{
    public double Celsius { get; }
    public Temperature(double celsius) =>
        Celsius = celsius is >= -273.15 ? celsius
            : throw new ArgumentOutOfRangeException(nameof(celsius));
}
```

## Common mistakes

- Public fields instead of properties, preventing validation or versioning.
- Leaking internal mutable collections via property getters.
- Using `internal` everywhere instead of designing clear public surfaces.

## Related concepts

- [csharp.classes](/concepts/classes.md)
- [csharp.interfaces](/concepts/interfaces.md)
