---
name: functional-programming-ts
description: Functional programming in TypeScript: pure functions, immutability, composition, pipe/compose, Option/Result. Use when: (1) User asks for functional style or FP concepts, (2) Refactoring to pure functions or immutable data, (3) User mentions pipe, compose, currying, functor, monad, Option, Either, (4) Reducing side effects or making code more testable.
author: Jirayu Suebwongphanudet
version: 1.0.0
triggers:
  - functional programming
  - pure functions / immutability
  - pipe / compose / currying
  - Option / Either / Result
---

# Functional Programming (TypeScript)

Apply functional programming concepts in TypeScript/JavaScript. Load the relevant reference for full detail and examples.

## Concept selection

| Goal or problem | Concept | Reference |
|-----------------|---------|-----------|
| Same input → same output, no hidden state | Pure functions | [references/core.md](references/core.md) |
| No mutation, predictable updates | Immutability | [references/core.md](references/core.md) |
| Keep I/O and mutation at edges | Isolate side effects | [references/core.md](references/core.md) |
| Functions that take or return functions | Higher-order functions | [references/core.md](references/core.md) |
| Chain transformations (f(g(x))) | Compose / pipe | [references/composition.md](references/composition.md) |
| Style without naming the argument | Point-free | [references/composition.md](references/composition.md) |
| Fix some arguments, get a new function | Currying / partial application | [references/composition.md](references/composition.md) |
| Optional value without null/undefined | Option / Maybe | [references/data-structures.md](references/data-structures.md) |
| Success or error without throwing | Either / Result | [references/data-structures.md](references/data-structures.md) |
| Update without mutating | Immutable updates | [references/data-structures.md](references/data-structures.md) |
| Recursive logic, trees, divide-and-conquer | Recursion | [references/recursion.md](references/recursion.md) |
| Walk structure and build one value | Fold / reduce | [references/recursion.md](references/recursion.md) |

## References by category

- **Core**: [references/core.md](references/core.md) — Pure functions, immutability, side effects, higher-order functions
- **Composition**: [references/composition.md](references/composition.md) — pipe, compose, point-free, currying
- **Data structures**: [references/data-structures.md](references/data-structures.md) — Option, Result, immutable updates
- **Recursion**: [references/recursion.md](references/recursion.md) — Recursion vs iteration, tail calls, fold/reduce

Load the specific reference when implementing or explaining that concept.

## Anti-patterns to avoid

- Do not over-abstract: prefer simple functions and clear names over clever one-liners.
- Use FP where it reduces bugs or improves clarity; avoid forcing it when a loop or a class is clearer.
- Do not hide side effects inside “pure” functions; isolate them at the edges.
