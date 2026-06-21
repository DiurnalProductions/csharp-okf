---
id: csharp.exception_patterns
type: concept
title: Common Exception Patterns
description: Idiomatic approaches for validation, wrapping, filtering, and global handling.
tags: ['csharp', 'errors', 'patterns']
prerequisites:
  - csharp.try_catch_finally
related:
  - csharp.cancellation_tokens
  - csharp.nullable_types
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Guard clauses, exception filters, middleware exception handlers, and dispose-safe patterns form everyday error strategy.

## Mental model

Validate early with `ArgumentNullException.ThrowIfNull`. Wrap lower-level exceptions preserving inner exceptions. Use `when` filters to distinguish cancellation from faults. ASP.NET Core uses exception middleware for HTTP mapping. `ProblemDetails` standardizes API errors. For libraries, document thrown exceptions. Prefer `TryParse` over `Parse` in hot paths. Global handlers log and fail fast for unhandled domain exceptions.

## Example

```csharp
ArgumentNullException.ThrowIfNull(input);

catch (Exception ex) when (ex is not OperationCanceledException)
{
    logger.LogError(ex, "Unexpected failure");
    throw;
}
```

## Common mistakes

- Returning null instead of throwing for unrecoverable contract violations without documenting.
- Mapping all exceptions to 500 without differentiation.
- Catching `OperationCanceledException` as generic failure.

## Related concepts

- [csharp.cancellation_tokens](/concepts/cancellation_tokens.md)
- [csharp.nullable_types](/concepts/nullable_types.md)
