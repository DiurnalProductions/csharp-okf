---
id: csharp.dictionary
type: concept
title: Dictionary<TKey, TValue>
description: Hash table mapping unique keys to values with fast lookup.
tags: ['csharp', 'collections', 'dictionary']
prerequisites:
  - csharp.list
related:
  - csharp.ienumerable
  - csharp.generic_classes
resource: https://learn.microsoft.com/en-us/dotnet/csharp/
timestamp: 2026-01-01
---

## Summary

`Dictionary<TKey,TValue>` provides average O(1) lookup using `GetHashCode` and `Equals` on keys.

## Mental model

Buckets store entries; collisions resolved by chaining. Keys must be immutable or stable hash codes while in dictionary. `TryGetValue` avoids double lookup. Enumeration order is undefined unless using `SortedDictionary`. `ConcurrentDictionary` adds thread safety. Reference type keys use reference equality unless overridden. Struct keys must implement equality correctly to avoid bucket clustering.

## Example

```csharp
var ages = new Dictionary<string, int>
{
    ["Ada"] = 36,
    ["Lin"] = 34
};

if (ages.TryGetValue("Ada", out var age))
    Console.WriteLine(age);
```

## Common mistakes

- Mutable keys whose hash code changes after insertion.
- Using `dict[key]` when `TryGetValue` is safer for missing keys.
- Assuming enumeration order matches insertion order (unless `OrderedDictionary` in newer .NET).

## Related concepts

- [csharp.ienumerable](/concepts/ienumerable.md)
- [csharp.generic_classes](/concepts/generic_classes.md)
