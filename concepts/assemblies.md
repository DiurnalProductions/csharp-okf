---
id: csharp.assemblies
type: concept
title: Assemblies
description: Deployment units containing IL, metadata, and resources—the .dll/.exe boundary.
tags: ['csharp', 'ecosystem', 'assemblies']
prerequisites:
  - csharp.namespaces
  - csharp.compilation_model
related:
  - csharp.nuget
  - csharp.clr
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

An assembly is the versioned unit of deployment, identity, and reference for the compiler and runtime.

## Mental model

Strong-name/signing, assembly version, and culture participate in binding. Reference assemblies allow compiling against API without implementation. Satellite assemblies hold localized resources. Reflection loads types from assemblies at runtime. InternalsVisibleTo shares `internal` across friend assemblies. Splitting into assemblies affects compile times, versioning, and deployment—not just folder organization.

## Example

```xml
<!-- Project reference -->
<ItemGroup>
  <ProjectReference Include="..\Core\Core.csproj" />
</ItemGroup>
```

## Common mistakes

- Circular assembly references breaking build.
- Exposing too much `public` API surface from every assembly.
- Ignoring assembly version binding in plugin hosts.

## Related concepts

- [csharp.nuget](/concepts/nuget.md)
- [csharp.clr](/concepts/clr.md)
