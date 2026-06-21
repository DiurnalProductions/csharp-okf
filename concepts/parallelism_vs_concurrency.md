---
id: csharp.parallelism_vs_concurrency
type: concept
title: Parallelism vs Concurrency
description: Distinguishing overlapping execution from simultaneous CPU-bound work.
tags: ['csharp', 'async', 'parallelism', 'threading']
prerequisites:
  - csharp.task
  - csharp.async_await
related:
  - csharp.synchronization_context
  - csharp.task
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Concurrency is structure; parallelism is simultaneous execution. Async enables concurrency without parallelism.

## Mental model

Concurrent code may interleave tasks on one or more threads—async I/O waits without blocking threads. Parallelism uses multiple cores simultaneously (`Parallel.ForEach`, PLINQ, multiple CPU-bound tasks). `Task.Run` moves CPU work to thread pool for parallelism but does not make I/O faster. Choose async for scalability under I/O load; choose parallel algorithms for CPU-bound batch processing with awareness of overhead and thread pool saturation.

## Example

```csharp
// Concurrent I/O:
var pages = await Task.WhenAll(urls.Select(u => client.GetStringAsync(u)));

// Parallel CPU:
Parallel.ForEach(data, item => Process(item));
```

## Common mistakes

- Expecting `async` to speed up CPU-bound work.
- Unbounded `Task.Run` spawning overwhelming thread pool.
- Using parallel loops on non-thread-safe shared state without synchronization.

## Related concepts

- [csharp.synchronization_context](/concepts/synchronization_context.md)
- [csharp.task](/concepts/task.md)
