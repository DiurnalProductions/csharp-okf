---
id: csharp.exceptions
type: concept
title: Exceptions
description: Structured error signaling via thrown exception objects unwinding the stack.
tags: ['csharp', 'errors', 'exceptions']
prerequisites:
  - csharp.methods
related:
  - csharp.try_catch_finally
  - csharp.error_propagation
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Exceptions represent exceptional conditions. The CLR walks stack frames running `finally` and matching `catch` blocks.

## Mental model

Throwing is expensive compared to normal control flow—use for exceptional cases, not expected outcomes. Exception objects carry message, inner exceptions, and stack traces (captured at throw site). Filtered catches (`when`) inspect exception state. `throw;` rethrows preserving stack trace; `throw ex;` resets it. Async/await marshals exceptions into faulted `Task` state. Custom exceptions should be `[Serializable]` only if remoting legacy matters—prefer clear type hierarchies.

## Example

```csharp
if (value < 0)
    throw new ArgumentOutOfRangeException(nameof(value));

try { Work(); }
catch (IOException ex)
{
    throw new InvalidOperationException("Work failed", ex);
}
```

## Common mistakes

- Using exceptions for routine control flow (e.g., parse failures in loops).
- Catching `Exception` too broadly and hiding bugs.
- Throwing new exception without inner exception losing context.

## Related concepts

- [csharp.try_catch_finally](/concepts/try_catch_finally.md)
- [csharp.error_propagation](/concepts/error_propagation.md)
