---
id: csharp.project_structure
type: concept
title: Project Structure
description: SDK-style projects, solution layout, and multi-project organization.
tags: ['csharp', 'ecosystem', 'tooling']
prerequisites:
  - csharp.assemblies
  - csharp.nuget
related:
  - csharp.namespaces
  - csharp.dependency_injection
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

Modern .NET uses SDK-style `.csproj` files with implicit defaults, solutions grouping projects, and clear separation of concerns.

## Mental model

A solution is a workspace container—not deployed. Projects target frameworks via `<TargetFramework>net8.0</TargetFramework>`. `Directory.Build.props` shares settings. Test, src, and build folders are conventions. `dotnet` CLI restores, builds, tests, packs. Source generators and analyzers run at compile time. Structure should reflect bounded contexts: domain, application, infrastructure, host.

## Example

```text
src/
  MyApp.Domain/
  MyApp.Application/
  MyApp.Infrastructure/
  MyApp.Web/
tests/
  MyApp.Tests/
```

## Common mistakes

- Monolithic projects when boundaries would clarify dependencies.
- Mixing test code in production projects.
- Ignoring `Nullable` and `ImplicitUsings` settings across projects.

## Related concepts

- [csharp.namespaces](/concepts/namespaces.md)
- [csharp.dependency_injection](/concepts/dependency_injection.md)
