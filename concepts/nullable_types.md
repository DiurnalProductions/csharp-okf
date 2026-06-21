---
id: csharp.nullable_types
type: concept
title: Nullable Types
description: Representing absence of value with nullable value types and nullable reference type annotations.
tags: ['csharp', 'fundamentals', 'types', 'null']
prerequisites:
  - csharp.type_system
  - csharp.value_types_vs_reference_types
related:
  - csharp.value_types_vs_reference_types
  - csharp.exception_patterns
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

C# offers `T?` for nullable value types and nullable reference type annotations (`string?`) to model possibly-null references at compile time.

## Mental model

Nullable value types (`int?`) are syntactic sugar for `Nullable<int>`, a struct wrapping a value plus a `HasValue` flag. Nullable reference types (NRT) are a compile-time annotation layer: `string` vs `string?` does not change runtime IL—the compiler emits warnings when you dereference without checking. The runtime can still produce null for either. Use null-forgiving (`!`), null-conditional (`?.`), and null-coalescing (`??`) operators to express intent. NRT shifts null-safety left to compile time rather than eliminating null at runtime.

## Example

```csharp
int? maybe = null;
if (maybe is int value)
    Console.WriteLine(value);

string? name = GetName();
int len = name?.Length ?? 0;
```

## Common mistakes

- Assuming NRT guarantees no `NullReferenceException` at runtime.
- Using `!` to silence warnings without a real invariant.
- Forgetting that `default(string?)` and `default(string)` are both null at runtime.

## Related concepts

- [csharp.value_types_vs_reference_types](/concepts/value_types_vs_reference_types.md)
- [csharp.exception_patterns](/concepts/exception_patterns.md)
