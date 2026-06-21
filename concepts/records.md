---
id: csharp.records
type: concept
title: Records
description: Reference or value types with built-in equality, immutability, and deconstruction support.
tags: ['csharp', 'oop', 'records', 'immutability']
prerequisites:
  - csharp.classes
  - csharp.value_types_vs_reference_types
related:
  - csharp.value_semantics
  - csharp.structs
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`record class` and `record struct` synthesize equality, `with` expressions, and positional syntax for data-centric types.

## Mental model

Records are still classes or structs at runtime—compiler generates `Equals`, `GetHashCode`, `ToString`, and copy methods. Value equality compares data members, not reference identity (for record classes). `with` creates shallow copies with mutations. Positional records generate constructor and properties from primary constructor syntax. Use records for DTOs and value-like aggregates; use classes when identity and lifecycle matter.

## Example

```csharp
public record Person(string Name, int Age);

var ada = new Person("Ada", 36);
var older = ada with { Age = 37 };
```

## Common mistakes

- Putting mutable reference types in records without defensive copies.
- Using records for entities with database identity semantics.
- Assuming `record struct` is always cheaper—it still copies on assignment.

## Related concepts

- [csharp.value_semantics](/concepts/value_semantics.md)
- [csharp.structs](/concepts/structs.md)
