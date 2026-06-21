---
id: csharp.nuget
type: concept
title: NuGet Packages
description: The package manager for distributing and consuming .NET libraries.
tags: ['csharp', 'ecosystem', 'nuget']
prerequisites:
  - csharp.assemblies
related:
  - csharp.project_structure
  - csharp.dependency_injection
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

NuGet delivers dependencies as packages restored into your project, recorded in the project file.

## Mental model

Package references resolve transitive dependencies into a graph locked by `packages.lock.json` optionally. Central Package Management consolidates versions. Sources include nuget.org and private feeds. Packages contain assemblies, build targets, and analyzers. Version ranges (`[1.0,2.0)`) control updates. Understanding package vs project references matters for trimming and AOT compatibility.

## Example

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Extensions.Logging" Version="8.0.0" />
</ItemGroup>
```

## Common mistakes

- Pinning no versions in libraries, causing downstream breaks.
- Committing `bin/obj` but not documenting required feeds.
- Adding packages for trivial functionality increasing attack surface.

## Related concepts

- [csharp.project_structure](/concepts/project_structure.md)
- [csharp.dependency_injection](/concepts/dependency_injection.md)
