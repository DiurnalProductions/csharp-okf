---
id: csharp.dependency_injection
type: concept
title: Dependency Injection Concepts
description: Inverting dependencies by supplying collaborators from a composition root.
tags: ['csharp', 'ecosystem', 'di', 'patterns']
prerequisites:
  - csharp.interfaces
  - csharp.classes
related:
  - csharp.project_structure
  - csharp.nuget
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

DI registers services (interfaces to implementations) in a container, resolving object graphs at runtime in ASP.NET Core and generic hosts.

## Mental model

Constructor injection is the default pattern—dependencies are explicit and immutable. Lifetimes: transient (new each resolve), scoped (per request/scope), singleton (one instance). Service descriptors map `typeof(I)` to implementation or factory. `IServiceProvider` builds graphs; avoid service locator in domain code. Generic hosting wires logging, configuration, and options. DI enables testing with fakes without changing consumers.

## Example

```csharp
builder.Services.AddScoped<IOrderRepo, SqlOrderRepo>();
builder.Services.AddSingleton<IClock, SystemClock>();

public class OrderService(IOrderRepo repo, IClock clock) { }
```

## Common mistakes

- Captive dependencies (singleton holding scoped service).
- Resolving scoped services from root provider.
- Registering concrete types without interfaces, hindering testing.

## Related concepts

- [csharp.project_structure](/concepts/project_structure.md)
- [csharp.nuget](/concepts/nuget.md)
