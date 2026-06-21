---
id: csharp.compilation_model
type: concept
title: Compilation Model
description: How C# source becomes assemblies through compile-time translation.
tags: ['csharp', 'runtime', 'compilation']
prerequisites: []
related:
  - csharp.il
  - csharp.assemblies
  - csharp.namespaces
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

C# compiles to IL in assemblies. Compilation is static, whole-program per project, with optional ahead-of-time and trimming in modern .NET.

## Mental model

The Roslyn compiler (`csc` / `dotnet build`) parses C#, performs semantic analysis against referenced assemblies, emits IL and metadata into a PE file (.dll/.exe). There is no interpreter for C# source at runtime. SDK-style projects reference target frameworks that provide reference assemblies—contracts without implementation. Native AOT and trimming are deployment optimizations but still begin from IL compilation. Errors are caught primarily at compile time because types are static.

## Example

```bash
dotnet new console -n Demo
dotnet build   # emits bin/Debug/net8.0/Demo.dll
```

## Common mistakes

- Expecting `#if DEBUG` blocks to exist at runtime—they are compile-time conditionals.
- Confusing compile-time constants with runtime configuration.
- Referencing implementation assemblies when only reference assemblies are needed for compilation.

## Related concepts

- [csharp.il](/concepts/il.md)
- [csharp.assemblies](/concepts/assemblies.md)
- [csharp.namespaces](/concepts/namespaces.md)
