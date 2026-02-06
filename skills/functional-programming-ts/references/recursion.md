# Recursion: recursion vs loops, tail calls, folds

## Recursion vs loops

Recursion: a function calls itself with a smaller input until a base case.

```typescript
function sum(n: number): number {
  if (n <= 0) return 0;
  return n + sum(n - 1);
}

function factorial(n: number): number {
  if (n <= 1) return 1;
  return n * factorial(n - 1);
}
```

Use recursion when the problem is naturally recursive (trees, nested structures, divide-and-conquer). Use iteration when you have a simple sequence or when stack depth is a concern (JS has no TCO in practice).

## Tail recursion and JS/TS limits

Tail recursion: the recursive call is the last thing the function does. Some languages optimize this to constant stack use; JavaScript engines generally do not. So deep recursion can still cause stack overflow.

```typescript
// Not tail recursive: work after the call
function sum(n: number): number {
  if (n <= 0) return 0;
  return n + sum(n - 1);  // addition after return
}

// Tail recursive: convert to accumulator
function sumTail(n: number, acc = 0): number {
  if (n <= 0) return acc;
  return sumTail(n - 1, acc + n);
}
```

Prefer iterative solutions (e.g. `for`, `while`, `reduce`) when you need guaranteed bounded stack usage in TS/JS.

## Fold / reduce

Fold (reduce) captures “walk a structure once and build a result.” Use instead of ad-hoc recursion when you’re combining elements.

```typescript
const sum = (arr: number[]) => arr.reduce((a, b) => a + b, 0);
const product = (arr: number[]) => arr.reduce((a, b) => a * b, 1);
const max = (arr: number[]) =>
  arr.reduce((a, b) => (a >= b ? a : b), -Infinity);

// Recursive fold on a tree
interface Tree<T> {
  value: T;
  children: Tree<T>[];
}
function foldTree<T, U>(fn: (v: T, children: U[]) => U, tree: Tree<T>): U {
  const childResults = tree.children.map((c) => foldTree(fn, c));
  return fn(tree.value, childResults);
}
```

When to use: any time you’re “combining” a list or tree into one value (sum, max, flatten, build a new structure).

## When to prefer recursion vs iteration in TS

- Prefer recursion: tree/graph traversal, recursive data (JSON, ASTs), divide-and-conquer, when the recursive version is much clearer.
- Prefer iteration: linear sequences, large inputs (avoid stack overflow), performance-critical paths. Use `reduce`/`fold` when you’re folding over a structure.

[← Back to SKILL](../SKILL.md)
