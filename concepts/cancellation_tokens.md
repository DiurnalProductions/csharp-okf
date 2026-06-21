---
id: csharp.cancellation_tokens
type: concept
title: Cancellation Tokens
description: Cooperative cancellation signaling for long-running and async operations.
tags: ['csharp', 'async', 'cancellation']
prerequisites:
  - csharp.task
  - csharp.async_await
related:
  - csharp.async_await
  - csharp.exception_patterns
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`CancellationToken` propagates cancellation requests; operations poll or register callbacks to stop cooperatively.

## Mental model

`CancellationTokenSource` owns the token and can signal cancel. Tokens are structs copied by value but share internal state. Library methods accept `CancellationToken` and throw `OperationCanceledException` when signaled—distinct from fault exceptions. Link tokens for timeouts (`CancelAfter`). Async methods should pass tokens through to I/O APIs. Cancellation is cooperative: code must observe the token; killing threads is not the model.

## Example

```csharp
using var cts = new CancellationTokenSource(TimeSpan.FromSeconds(5));
try
{
    await LongRunningAsync(cts.Token);
}
catch (OperationCanceledException) when (cts.IsCancellationRequested)
{
    // expected cancellation
}
```

## Common mistakes

- Swallowing `OperationCanceledException` without distinguishing fault vs cancel.
- Not passing tokens through nested calls.
- Using cancellation as exception flow control for business logic.

## Related concepts

- [csharp.async_await](/concepts/async_await.md)
- [csharp.exception_patterns](/concepts/exception_patterns.md)
