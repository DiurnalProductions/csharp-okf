---
id: csharp.try_catch_finally
type: concept
title: try / catch / finally
description: Structured exception handling blocks for recovery and cleanup.
tags: ['csharp', 'errors', 'exceptions']
prerequisites:
  - csharp.exceptions
related:
  - csharp.error_propagation
  - csharp.exception_patterns
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`try` guards code; `catch` handles specific exceptions; `finally` always runs for cleanup.

## Mental model

When an exception is thrown, CLR searches up the stack for compatible catch clauses. `finally` runs on both normal and exceptional exit—used for releasing resources though `using` is preferred. Multiple catches ordered from specific to general. `catch` without type catches all exceptions (avoid). Async methods compile `try/catch` into state machine fault paths. Nested tries build deterministic cleanup ordering.

## Example

```csharp
try
{
    var data = await ReadAsync();
    Process(data);
}
catch (JsonException ex)
{
    Log(ex);
}
finally
{
    Cleanup();
}
```

## Common mistakes

- Empty catch blocks silencing failures.
- Catching and rethrowing with `throw ex` losing stack trace.
- Putting return statements in `finally` masking exceptions.

## Related concepts

- [csharp.error_propagation](/concepts/error_propagation.md)
- [csharp.exception_patterns](/concepts/exception_patterns.md)
