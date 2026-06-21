---
id: csharp.namespaces
type: concept
title: Namespaces
description: Logical grouping of types to avoid naming collisions and organize APIs.
tags: ['csharp', 'ecosystem', 'organization']
prerequisites: []
related:
  - csharp.assemblies
  - csharp.project_structure
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Namespaces map to CLR type names (`Company.Product.Feature.Type`) and are declared with `namespace` blocks or file-scoped namespaces.

## Mental model

Namespaces are compile-time organizational units—not deployment boundaries. `using` directives import names for convenience; `global using` applies project-wide. File-scoped namespace (C# 10) reduces indentation. Nested namespaces can be dotted in one declaration. External code sees fully qualified names in metadata. Namespaces do not enforce access control—`internal` does across an assembly.

## Example

```csharp
namespace MyApp.Services;

public class EmailService { }
```

## Common mistakes

- Mirroring folder structure in namespaces without consistency discipline.
- Over-nesting namespaces (`Company.Product.Module.Sub.Area`).
- Confusing namespace with assembly boundary.

## Related concepts

- [csharp.assemblies](/concepts/assemblies.md)
- [csharp.project_structure](/concepts/project_structure.md)
