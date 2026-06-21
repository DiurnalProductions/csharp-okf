---
id: csharp.il
type: concept
title: Intermediate Language (IL)
description: The stack-based bytecode C# compiles into, executed by the CLR.
tags: ['csharp', 'runtime', 'il', 'clr']
prerequisites:
  - csharp.compilation_model
related:
  - csharp.clr
  - csharp.assemblies
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

IL (CIL/MSIL) is the portable instruction set of .NET. It abstracts CPU specifics and enables language interoperability.

## Mental model

IL instructions operate on a virtual stack: `ldarg`, `call`, `box`, `newobj`, etc. Metadata tables describe types, methods, fields, and attributes—enabling reflection and generics. The JIT compiler translates IL to native machine code per method on first invocation (unless AOT). View IL with `ildasm` or ILSpy. Language features like `async/await`, `foreach`, and `using` are often lowered to IL patterns (state machines, try/finally) by the compiler.

## Example

```csharp
// C# lambda:
Func<int, int> square = x => x * x;
// Compiler emits a display class + method for closure capture when needed
```

## Common mistakes

- Assuming IL opcodes map 1:1 to C# statements.
- Ignoring metadata when debugging versioning or linking issues.
- Expecting identical IL across compiler versions for all constructs.

## Related concepts

- [csharp.clr](/concepts/clr.md)
- [csharp.assemblies](/concepts/assemblies.md)
