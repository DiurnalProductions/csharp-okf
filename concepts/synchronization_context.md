---
id: csharp.synchronization_context
type: concept
title: Synchronization Context
description: Mechanism determining where async continuations resume after await.
tags: ['csharp', 'async', 'threading']
prerequisites:
  - csharp.async_await
related:
  - csharp.parallelism_vs_concurrency
  - csharp.async_await
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

UI frameworks install a synchronization context so awaits return to the UI thread; thread pool contexts do not capture.

## Mental model

By default, `await` captures `SynchronizationContext.Current` and posts continuations back. ASP.NET Core and console apps typically have no special context—continuations run on thread pool threads. Deadlocks occur when a UI/sync context thread blocks waiting for a task that needs that same thread to complete. `ConfigureAwait(false)` in libraries avoids imposing caller context. Understanding context explains UI threading rules and why blocking is harmful.

## Example

```csharp
// Library code:
await SomeIoAsync().ConfigureAwait(false);
// Avoids forcing UI thread resume
```

## Common mistakes

- Blocking UI thread with `.Result` while awaiting needs UI thread.
- Using `ConfigureAwait(false)` in app code that must update UI after await.
- Assuming every await yields a thread switch (often it continues synchronously if task completed).

## Related concepts

- [csharp.parallelism_vs_concurrency](/concepts/parallelism_vs_concurrency.md)
- [csharp.async_await](/concepts/async_await.md)
