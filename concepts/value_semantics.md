---
id: csharp.value_semantics
type: concept
title: Value Semantics
description: Types where equality and copying are based on data rather than identity.
tags: ['csharp', 'memory', 'structs', 'records']
prerequisites:
  - csharp.structs
  - csharp.value_types_vs_reference_types
related:
  - csharp.records
  - csharp.span
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Value semantics mean assignment copies data and equality compares contents—typical for structs and records.

## Mental model

Value semantic types should implement consistent `Equals`, `==`, and `GetHashCode` based on fields. Immutability makes shared copies safe. Shallow copy via assignment; deep copy requires explicit logic if containing reference types. Records default to value equality. Classes can mimic value semantics but remain reference allocated—`record class` bridges both worlds. Choose value semantics for small immutable measurements; identity for entities with lifecycle.

## Example

```csharp
record struct Point(int X, int Y);

var a = new Point(1, 2);
var b = a with { X = 3 };
Console.WriteLine(a == b); // false — different data
```

## Common mistakes

- Value semantic struct containing mutable reference fields shared across copies.
- Implementing value equality on mutable classes inconsistently.
- Deep copying large graphs unintentionally via record `with`.

## Related concepts

- [csharp.records](/concepts/records.md)
- [csharp.span](/concepts/span.md)
