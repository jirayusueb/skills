# Core: Pure Functions, Immutability, Side Effects, HOFs

## Pure functions

Same inputs always produce the same output. No side effects (no mutation, no I/O, no shared state).

```typescript
// Pure: same (x, y) → same result, no side effects
function add(x: number, y: number): number {
  return x + y;
}

// Impure: depends on external state, has side effect
let total = 0;
function addToTotal(x: number): number {
  total += x;  // mutation
  return total;
}
```

Use pure functions for logic that should be testable and predictable. Isolate impure code at the edges (API calls, DOM, logging).

## Immutability

Do not mutate existing data; produce new values. In TypeScript: prefer `const`, `readonly`, and copies.

```typescript
// Prefer const
const items = [1, 2, 3];

// New array instead of mutating
const withFour = [...items, 4];

// readonly for interfaces
interface User {
  readonly id: number;
  readonly name: string;
}

// Updating: spread into new object
const updated = { ...user, name: 'New Name' };
```

When to use: shared state, concurrency, predictable updates. Avoid deep nesting with manual spread; consider libraries (Immer) or structural sharing if needed.

## Isolating side effects

Push I/O and mutation to the boundaries. Keep core logic pure and call side-effecting code from a thin layer.

```typescript
// Pure core
function validateAndFormat(name: string): string | null {
  const trimmed = name.trim();
  return trimmed.length > 0 ? trimmed : null;
}

// Side effect at the edge
function saveUser(name: string): void {
  const result = validateAndFormat(name);
  if (result !== null) {
    database.insert({ name: result });  // side effect
  }
}
```

## Higher-order functions (HOFs)

Functions that take or return functions. Use for abstraction and reuse.

```typescript
type Predicate<T> = (x: T) => boolean;
type Mapper<T, U> = (x: T) => U;

function filter<T>(pred: Predicate<T>, arr: T[]): T[] {
  return arr.filter(pred);
}

function map<T, U>(fn: Mapper<T, U>, arr: T[]): U[] {
  return arr.map(fn);
}

// Custom HOF: wrap with logging
function withLog<T, U>(fn: (x: T) => U, label: string): (x: T) => U {
  return (x: T) => {
    console.log(label, x);
    return fn(x);
  };
}
```

Built-in HOFs: `map`, `filter`, `reduce`, `find`, `some`, `every`. Use them instead of manual loops when they clarify intent.

[← Back to SKILL](../SKILL.md)
