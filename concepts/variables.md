---
id: csharp.variables
type: concept
title: Variables
description: Named storage locations for values, declared with explicit or inferred types.
tags: ['csharp', 'fundamentals', 'types']
prerequisites: []
related:
  - csharp.type_system
  - csharp.methods
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Variables bind names to values in a scope. C# requires every variable to have a compile-time type, whether written explicitly or inferred with `var`.

## Mental model

When you declare a variable, the compiler records a name-to-type binding in the current scope. At runtime, value-type variables hold their data inline in the stack frame (or in registers); reference-type variables hold a pointer-sized reference to an object on the heap. `var` does not create a dynamic variable—it still resolves to a concrete static type at compile time. Local variables must be definitely assigned before use; fields get default values.

## Example

```csharp
int count = 42;           // explicit type
var name = "Ada";         // inferred as string
const double Pi = 3.14159; // compile-time constant

void Demo()
{
    int x;       // default 0
    string? s;   // nullable reference type, default null
    // Console.WriteLine(x + s.Length); // error: s not definitely assigned
}
```

## Common mistakes

- Treating `var` as `dynamic`—it is still statically typed.
- Assuming uninitialized locals default to null for value types (they are zero-initialized but the compiler may still reject use before assignment).
- Using `var` when the inferred type is unclear to readers (e.g., `var result = GetData()` hiding important type information).

## Related concepts

- [csharp.type_system](/concepts/type_system.md)
- [csharp.methods](/concepts/methods.md)
