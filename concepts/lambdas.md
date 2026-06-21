---
id: csharp.lambdas
type: concept
title: Lambda Expressions
description: Inline anonymous functions used for concise delegates and expression trees.
tags: ['csharp', 'fundamentals', 'lambdas', 'functional']
prerequisites:
  - csharp.delegates
related:
  - csharp.closures
  - csharp.linq
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Lambdas (`=>`) create delegate instances or expression trees depending on target type.

## Mental model

Statement lambdas use braces; expression lambdas return a single expression. Target typing infers parameter types. When assigned to `Expression<Func<...>>`, the compiler builds an expression tree instead of IL. Lambdas that capture locals become instance methods on a generated display class with fields for captures. This allocation is usually small but matters in hot paths. `static` lambdas (C# 9+) avoid capturing `this` accidentally.

## Example

```csharp
List<int> nums = new() { 1, 2, 3 };
nums.Sort((a, b) => b.CompareTo(a)); // descending

Func<int, int> sq = static x => x * x; // no accidental this capture
```

## Common mistakes

- Capturing loop variables incorrectly in older C# (fixed in C# 5+ for `foreach`).
- Using lambdas where a method group would be clearer and allocation-free.
- Mixing expression trees and delegates without noticing different semantics.

## Related concepts

- [csharp.closures](/concepts/closures.md)
- [csharp.linq](/concepts/linq.md)
