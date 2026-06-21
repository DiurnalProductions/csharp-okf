---
id: csharp.error_propagation
type: concept
title: Error Propagation
description: How exceptions and results flow through call stacks and async boundaries.
tags: ['csharp', 'errors', 'async']
prerequisites:
  - csharp.exceptions
  - csharp.try_catch_finally
related:
  - csharp.async_await
  - csharp.exception_patterns
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Unhandled exceptions propagate to callers; async methods store exceptions on Tasks until awaited.

## Mental model

Synchronous propagation unwinds the stack immediately. In async code, thrown exceptions mark the returned `Task` as faulted—the exception surfaces at the `await`. AggregateException appears with `Task.Wait` on multiple failures. Result types (`Result<T>`, manual unions) offer explicit error channels without exceptions. Choose exceptions for truly exceptional failures; use return values or `OneOf` patterns for expected errors in high-throughput paths.

## Example

```csharp
public async Task<User> GetUserAsync(Guid id)
{
    // Exception here becomes faulted Task, not immediate throw to caller
    return await repo.FindAsync(id)
        ?? throw new KeyNotFoundException(id.ToString());
}
```

## Common mistakes

- Not awaiting tasks, leaving faulted tasks unobserved.
- Assuming `AggregateException` in normal async/await (usually unwrapped at await).
- Mixing exception and error-code styles inconsistently across layers.

## Related concepts

- [csharp.async_await](/concepts/async_await.md)
- [csharp.exception_patterns](/concepts/exception_patterns.md)
