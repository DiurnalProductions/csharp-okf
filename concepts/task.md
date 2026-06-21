---
id: csharp.task
type: concept
title: Task and Task-Based Asynchrony
description: Representations of asynchronous operations and their eventual results.
tags: ['csharp', 'async', 'task', 'concurrency']
prerequisites:
  - csharp.delegates
related:
  - csharp.async_await
  - csharp.cancellation_tokens
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`Task` and `Task<T>` represent asynchronous work cooperatively scheduled on the thread pool by default.

## Mental model

A `Task` is a reference object representing an operation that may be running, completed, faulted, or canceled. Continuations attach via `ContinueWith` or `await`. `Task.Run` queues thread pool work—use for CPU-bound offload, not for pretending I/O is async. `ValueTask` reduces allocation for often-synchronous paths. Tasks are composable: `WhenAll`, `WhenAny`. Understanding Task state explains exception marshaling and why unobserved task exceptions can tear down the process in some hosts.

## Example

```csharp
Task<int> ComputeAsync() =>
    Task.Run(() => Enumerable.Range(1, 1000).Sum());

var sum = await ComputeAsync();
```

## Common mistakes

- Blocking on `.Result` or `.Wait()` causing deadlocks with synchronization context.
- Using `Task.Run` for trivial work, adding overhead.
- Fire-and-forget tasks without observing exceptions.

## Related concepts

- [csharp.async_await](/concepts/async_await.md)
- [csharp.cancellation_tokens](/concepts/cancellation_tokens.md)
