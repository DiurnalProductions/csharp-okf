---
id: csharp.structs
type: concept
title: Structs
description: Value types for compact, copy-by-value data with optional interface implementation.
tags: ['csharp', 'oop', 'structs', 'value-types']
prerequisites:
  - csharp.value_types_vs_reference_types
  - csharp.classes
related:
  - csharp.value_semantics
  - csharp.records
  - csharp.span
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Structs are value types stored inline with their containing context; copying is bitwise by default.

## Mental model

Structs live on the stack as locals or inline in containing objects. Default constructor zero-initializes (C# 10+ allows explicit parameterless constructors). Implementing interfaces boxes when cast to interface type. Large structs hurt performance due to copy cost—Microsoft guidance often suggests keeping structs under ~16 bytes. `readonly struct` prevents mutating methods from modifying `this`. `ref struct` types (e.g., `Span<T>`) must stay on the stack.

## Example

```csharp
readonly struct Vector2
{
    public double X { get; init; }
    public double Y { get; init; }
    public double Length => Math.Sqrt(X * X + Y * Y);
}
```

## Common mistakes

- Mutable structs with methods that modify `this` without reassigning in collections.
- Boxing structs through interface calls in hot paths.
- Using struct for types that need identity semantics.

## Related concepts

- [csharp.value_semantics](/concepts/value_semantics.md)
- [csharp.records](/concepts/records.md)
- [csharp.span](/concepts/span.md)
