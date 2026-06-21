# C# Knowledge Pack

C# is **a statically typed language compiled into IL and executed by the .NET runtime.**

This OKF knowledge bundle is a plug-and-play graph of C# and .NET concepts for OKF-compatible viewers. Each concept lives in [`concepts/`](concepts/) as a markdown file with YAML frontmatter. Relationships are expressed through `prerequisites` (learning order) and `related` (cross-links).

---

## Start here

If you are new to C# or .NET, begin with these entry concepts:

* [Variables](concepts/variables.md) — names, types, and scope
* [Compilation Model](concepts/compilation_model.md) — how source becomes assemblies
* [Namespaces](concepts/namespaces.md) — organizing types in code

Then follow the recommended progression below. Each concept builds on its prerequisites; the graph is a directed acyclic graph (DAG) with no circular dependencies.

---

## Recommended learning progression

### Phase 1 — Language fundamentals

1. [Variables](concepts/variables.md)
2. [Type System Fundamentals](concepts/type_system.md)
3. [Value Types vs Reference Types](concepts/value_types_vs_reference_types.md)
4. [Nullable Types](concepts/nullable_types.md)
5. [Boxing and Unboxing](concepts/boxing_and_unboxing.md)
6. [Methods](concepts/methods.md)
7. [Overload Resolution](concepts/overload_resolution.md)
8. [Delegates](concepts/delegates.md)
9. [Lambda Expressions](concepts/lambdas.md)
10. [Closures](concepts/closures.md)

### Phase 2 — Object-oriented system

11. [Classes](concepts/classes.md)
12. [Structs](concepts/structs.md)
13. [Encapsulation](concepts/encapsulation.md)
14. [Interfaces](concepts/interfaces.md)
15. [Inheritance](concepts/inheritance.md)
16. [Polymorphism](concepts/polymorphism.md)
17. [Records](concepts/records.md)
18. [Value Semantics](concepts/value_semantics.md)

### Phase 3 — Generics and collections

19. [Generic Classes](concepts/generic_classes.md)
20. [Generic Methods](concepts/generic_methods.md)
21. [Generic Constraints](concepts/generic_constraints.md)
22. [Covariance and Contravariance](concepts/variance.md)
23. [Arrays](concepts/arrays.md)
24. [IEnumerable and Iteration](concepts/ienumerable.md)
25. [List&lt;T&gt;](concepts/list.md)
26. [Dictionary&lt;TKey, TValue&gt;](concepts/dictionary.md)
27. [LINQ Mental Model](concepts/linq.md)
28. [Deferred Execution](concepts/deferred_execution.md)

### Phase 4 — Async programming

29. [Task and Task-Based Asynchrony](concepts/task.md)
30. [async and await](concepts/async_await.md)
31. [Synchronization Context](concepts/synchronization_context.md)
32. [Parallelism vs Concurrency](concepts/parallelism_vs_concurrency.md)
33. [Cancellation Tokens](concepts/cancellation_tokens.md)

### Phase 5 — Runtime and memory model

34. [Intermediate Language (IL)](concepts/il.md)
35. [Common Language Runtime (CLR)](concepts/clr.md)
36. [Stack vs Heap](concepts/stack_vs_heap.md)
37. [Memory Management Fundamentals](concepts/memory_management.md)
38. [Garbage Collection](concepts/garbage_collection.md)
39. [Span&lt;T&gt; and Memory&lt;T&gt;](concepts/span.md)
40. [Allocations and GC Pressure](concepts/allocations.md)

### Phase 6 — Exception handling

41. [Exceptions](concepts/exceptions.md)
42. [try / catch / finally](concepts/try_catch_finally.md)
43. [Error Propagation](concepts/error_propagation.md)
44. [Common Exception Patterns](concepts/exception_patterns.md)

### Phase 7 — Ecosystem and tooling

45. [Assemblies](concepts/assemblies.md)
46. [NuGet Packages](concepts/nuget.md)
47. [Project Structure](concepts/project_structure.md)
48. [Dependency Injection Concepts](concepts/dependency_injection.md)

---

## Concept groups

### Language fundamentals

* [Variables](concepts/variables.md) — named storage with static typing
* [Type System Fundamentals](concepts/type_system.md) — compile-time type checking
* [Value Types vs Reference Types](concepts/value_types_vs_reference_types.md) — the core memory and assignment split
* [Nullable Types](concepts/nullable_types.md) — modeling absence of value
* [Boxing and Unboxing](concepts/boxing_and_unboxing.md) — value-to-reference conversions on the heap
* [Methods](concepts/methods.md) — behavior units with parameters and returns
* [Overload Resolution](concepts/overload_resolution.md) — compile-time method selection
* [Delegates](concepts/delegates.md) — type-safe function references
* [Lambda Expressions](concepts/lambdas.md) — concise anonymous functions
* [Closures](concepts/closures.md) — captured variables and extended lifetimes

### Object-oriented system

* [Classes](concepts/classes.md) — reference types with identity
* [Structs](concepts/structs.md) — value types for compact data
* [Encapsulation](concepts/encapsulation.md) — access control and invariants
* [Interfaces](concepts/interfaces.md) — behavioral contracts
* [Inheritance](concepts/inheritance.md) — specialization through derivation
* [Polymorphism](concepts/polymorphism.md) — uniform treatment of specialized types
* [Records](concepts/records.md) — data-centric types with value equality
* [Value Semantics](concepts/value_semantics.md) — equality and copying by data

### Generics and collections

* [Generic Classes](concepts/generic_classes.md) — reified type-parameterized types
* [Generic Methods](concepts/generic_methods.md) — type-inferred algorithms
* [Generic Constraints](concepts/generic_constraints.md) — bounds on type parameters
* [Covariance and Contravariance](concepts/variance.md) — subtyping rules for generic interfaces
* [Arrays](concepts/arrays.md) — fixed-length indexed collections
* [IEnumerable and Iteration](concepts/ienumerable.md) — sequence abstraction and foreach
* [List&lt;T&gt;](concepts/list.md) — resizable array-backed lists
* [Dictionary&lt;TKey, TValue&gt;](concepts/dictionary.md) — hash-based key-value maps
* [LINQ Mental Model](concepts/linq.md) — composable query operators
* [Deferred Execution](concepts/deferred_execution.md) — lazy evaluation in LINQ pipelines

### Async programming

* [Task and Task-Based Asynchrony](concepts/task.md) — asynchronous operation representation
* [async and await](concepts/async_await.md) — cooperative suspension without blocking
* [Synchronization Context](concepts/synchronization_context.md) — continuation scheduling
* [Parallelism vs Concurrency](concepts/parallelism_vs_concurrency.md) — overlapping vs simultaneous execution
* [Cancellation Tokens](concepts/cancellation_tokens.md) — cooperative cancellation signaling

### Runtime and memory model

* [Compilation Model](concepts/compilation_model.md) — source to IL translation
* [Intermediate Language (IL)](concepts/il.md) — .NET bytecode
* [Common Language Runtime (CLR)](concepts/clr.md) — execution engine
* [Stack vs Heap](concepts/stack_vs_heap.md) — where data lives
* [Memory Management Fundamentals](concepts/memory_management.md) — allocation and reclamation model
* [Garbage Collection](concepts/garbage_collection.md) — generational automatic GC
* [Span&lt;T&gt; and Memory&lt;T&gt;](concepts/span.md) — low-allocation memory views
* [Allocations and GC Pressure](concepts/allocations.md) — performance impact of heap churn

### Ecosystem and tooling

* [Namespaces](concepts/namespaces.md) — logical type organization
* [Assemblies](concepts/assemblies.md) — deployment and versioning units
* [NuGet Packages](concepts/nuget.md) — package distribution and restore
* [Project Structure](concepts/project_structure.md) — SDK-style projects and solutions
* [Dependency Injection Concepts](concepts/dependency_injection.md) — inversion of control in .NET hosts

### Exception handling

* [Exceptions](concepts/exceptions.md) — structured error signaling
* [try / catch / finally](concepts/try_catch_finally.md) — handling and cleanup blocks
* [Error Propagation](concepts/error_propagation.md) — sync and async error flow
* [Common Exception Patterns](concepts/exception_patterns.md) — idiomatic error strategies

---

## Key themes

| Theme | Concepts to emphasize |
|-------|----------------------|
| Static typing and IL | Compilation, IL, CLR — C# is compiled, not interpreted |
| Value vs reference | Value types, reference types, boxing, stack vs heap, structs vs classes |
| Reified generics | Generic classes differ from type-erased systems like Java |
| LINQ as query algebra | IEnumerable, LINQ, deferred execution — lazy pipelines |
| Cooperative async | Task, async/await — non-blocking, not automatic parallelism |
| CLR and GC | Memory management, garbage collection, allocations shape runtime behavior |
| Records and structs | Different semantics from classes — value equality vs identity |

---

## Bundle metadata

See [`okf.json`](okf.json) for pack identity, version, and entry point.
