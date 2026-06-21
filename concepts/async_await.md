---
id: csharp.async_await
type: concept
title: async and await
description: Compiler-supported cooperative suspension without blocking threads.
tags: ['csharp', 'async', 'task']
prerequisites:
  - csharp.task
related:
  - csharp.synchronization_context
  - csharp.cancellation_tokens
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`async`/`await` rewrites methods into state machines that resume on continuations when awaited tasks complete.

## Mental model

When you `await`, the compiler splits the method at suspension points. If the awaited task is incomplete, the method returns a `Task` to its caller and registers a continuation. When complete, the continuation resumes—often on the captured synchronization context (UI thread). No extra thread is blocked during I/O waits. `async void` is fire-and-forget except for events. `ConfigureAwait(false)` avoids context capture in library code. Async is cooperative: it does not parallelize unless combined with multiple tasks or `Parallel`.

## Example

```csharp
public async Task<string> GetPageAsync(HttpClient client, string url)
{
    var response = await client.GetAsync(url);
    response.EnsureSuccessStatusCode();
    return await response.Content.ReadAsStringAsync();
}
```

## Common mistakes

- `async void` swallowing exceptions in hard-to-debug ways.
- Awaiting inside tight loops instead of batching with `Task.WhenAll`.
- Marking every method `async` when it does no awaiting.

## Related concepts

- [csharp.synchronization_context](/concepts/synchronization_context.md)
- [csharp.cancellation_tokens](/concepts/cancellation_tokens.md)
