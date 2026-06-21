---
id: csharp.overload_resolution
type: concept
title: Overload Resolution
description: How the compiler selects the best matching method overload for a call site.
tags: ['csharp', 'fundamentals', 'methods']
prerequisites:
  - csharp.methods
related:
  - csharp.methods
  - csharp.generic_methods
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Given multiple overloads, the compiler ranks candidates by applicability, better conversion, and specificity rules.

## Mental model

Overload resolution happens at compile time. Candidates must be applicable (argument count/types). Numeric promotions, implicit conversions, and `params` arrays participate. Generic methods undergo type inference. When an ambiguity remains, you get a compile error—not runtime dispatch. Optional parameters and named arguments are resolved at compile time. Explicit interface implementation can hide overload sets from class references.

## Example

```csharp
void Print(int x) => Console.WriteLine(x);
void Print(string s) => Console.WriteLine(s);

Print(42);      // int overload
Print("hi");    // string overload
```

## Common mistakes

- Relying on overload resolution between `int` and `double` without understanding promotion.
- Creating ambiguous overloads differing only by `params` vs array.
- Expecting runtime overload choice based on dynamic types without `dynamic`.

## Related concepts

- [csharp.methods](/concepts/methods.md)
- [csharp.generic_methods](/concepts/generic_methods.md)
