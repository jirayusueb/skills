# Composition: pipe, compose, point-free, currying

## Compose (right to left)

Apply functions in sequence: `compose(f, g)(x)` === `f(g(x))`.

```typescript
function compose<A, B, C>(f: (b: B) => C, g: (a: A) => B): (a: A) => C {
  return (a: A) => f(g(a));
}

// Multiple arity
function compose2<T>(...fns: Array<(x: T) => T>): (x: T) => T {
  return (x: T) => fns.reduceRight((acc, fn) => fn(acc), x);
}

const trim = (s: string) => s.trim();
const upper = (s: string) => s.toUpperCase();
const exclaim = (s: string) => s + '!';
const greet = compose2(exclaim, upper, trim);
greet('  hello '); // "HELLO !"
```

## Pipe (left to right)

Same idea as compose but order matches reading order: `pipe(g, f)(x)` === `f(g(x))`.

```typescript
function pipe<A, B, C>(f: (a: A) => B, g: (b: B) => C): (a: A) => C {
  return (a: A) => g(f(a));
}

function pipe2<T>(...fns: Array<(x: T) => T>): (x: T) => T {
  return (x: T) => fns.reduce((acc, fn) => fn(acc), x);
}

const clean = pipe2(trim, upper, exclaim);
clean('  hello '); // "HELLO !"
```

Use pipe when you have a linear pipeline of steps; use compose when you think in “inner to outer” transformations.

## Point-free style

Define functions without naming the argument when it’s just “pass through”.

```typescript
const double = (n: number) => n * 2;
const numbers = [1, 2, 3];

// Point-free: pass the function reference
const doubled = numbers.map(double);

// Not point-free: argument named
const doubled2 = numbers.map((n) => double(n));
```

Use point-free when it improves readability; avoid when it obscures intent.

## Currying and partial application

Currying: a function of N arguments becomes a chain of 1-argument functions. Partial application: fix some arguments and get a function that takes the rest.

```typescript
function curry2<A, B, R>(fn: (a: A, b: B) => R): (a: A) => (b: B) => R {
  return (a: A) => (b: B) => fn(a, b);
}

const add = (a: number, b: number) => a + b;
const curriedAdd = curry2(add);
curriedAdd(1)(2); // 3

// Partial application (no full curry)
const addTen = (n: number) => add(10, n);
```

Use currying when you want to pass “partially applied” functions (e.g. into `map`). Use simple partial application when you only need to fix one or two arguments.

## When composition helps vs hurts

- Helps: linear data flow, reuse of small functions, clear pipelines (e.g. parse → validate → transform).
- Hurts: long pipe/compose chains, hard-to-debug one-liners, or when a named function would be clearer. Prefer a few well-named steps over a single dense composition.

[← Back to SKILL](../SKILL.md)
