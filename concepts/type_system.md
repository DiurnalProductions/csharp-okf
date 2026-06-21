---
id: csharp.type_system
type: concept
title: Type System Fundamentals
description: C# is statically typed: every expression has a compile-time type checked by the compiler.
tags: ['csharp', 'fundamentals', 'types']
prerequisites:
  - csharp.variables
related:
  - csharp.value_types_vs_reference_types
  - csharp.nullable_types
  - csharp.generic_classes
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

C#'s type system partitions types into value types and reference types, supports generics, nullable annotations, and compile-time type checking with limited type inference.

## Mental model

The compiler builds a type graph for your program. Every variable, parameter, return value, and expression participates in this graph. Assignments and method calls are validated at compile time—there is no implicit conversion unless the language defines one. Types flow through overload resolution, generic inference, and pattern matching. Understanding whether a type is a value or reference kind is the foundation for everything else in C#.

## Example

```csharp
object obj = 42;        // boxing: int → object
int n = (int)obj;       // unboxing with cast

string[] names = { "a", "b" };
IEnumerable<string> seq = names; // array is IEnumerable<string>
```

## Common mistakes

- Confusing compile-time types with runtime types when generics and inheritance interact.
- Assuming all collections are covariant (they are not—`List<Dog>` is not a `List<Animal>`).
- Ignoring nullable reference type warnings as stylistic rather than semantic.

## Related concepts

- [csharp.value_types_vs_reference_types](/concepts/value_types_vs_reference_types.md)
- [csharp.nullable_types](/concepts/nullable_types.md)
- [csharp.generic_classes](/concepts/generic_classes.md)
