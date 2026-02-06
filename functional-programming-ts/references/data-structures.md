# Data structures: Option/Maybe, Either/Result, immutable updates

## Option / Maybe (optional values without null)

Model “might be missing” explicitly instead of using `null` or `undefined`.

```typescript
type Option<T> =
  | { kind: 'some'; value: T }
  | { kind: 'none' };

const some = <T>(value: T): Option<T> => ({ kind: 'some', value });
const none = <T>(): Option<T> => ({ kind: 'none' });

function mapOption<T, U>(fn: (x: T) => U, opt: Option<T>): Option<U> {
  return opt.kind === 'some' ? some(fn(opt.value)) : none();
}

function getOrElse<T>(opt: Option<T>, fallback: T): T {
  return opt.kind === 'some' ? opt.value : fallback;
}

// Usage
const findUser = (id: number): Option<User> => { /* ... */ };
const name = mapOption((u) => u.name, findUser(1));
getOrElse(name, 'Unknown');
```

When to use: when “missing” is a normal case and you want to force handling it. When a simple `if (x != null)` is enough, optional chaining (`?.`) or null checks are fine.

## Either / Result (success or error)

Model a result that is either a value or an error, without throwing.

```typescript
type Result<E, A> =
  | { kind: 'ok'; value: A }
  | { kind: 'err'; error: E };

const ok = <E, A>(value: A): Result<E, A> => ({ kind: 'ok', value });
const err = <E, A>(error: E): Result<E, A> => ({ kind: 'err', error });

function mapResult<E, A, B>(fn: (a: A) => B, r: Result<E, A>): Result<E, B> {
  return r.kind === 'ok' ? ok(fn(r.value)) : r;
}

function getOrElseResult<E, A>(r: Result<E, A>, fallback: A): A {
  return r.kind === 'ok' ? r.value : fallback;
}
```

Use Result for expected failures (validation, parsing, domain errors). Use throw for truly exceptional cases if your team prefers.

## Immutable updates

Avoid mutating objects and arrays; create new copies. Use spread and (if needed) structural sharing or a library.

```typescript
// Object: spread
const state = { count: 0, name: 'foo' };
const next = { ...state, count: state.count + 1 };

// Array: spread, filter, map
const arr = [1, 2, 3];
const added = [...arr, 4];
const removed = arr.filter((x) => x !== 2);
const updated = arr.map((x) => (x === 2 ? 20 : x));

// Nested: spread at each level
const nested = { a: { b: 1 } };
const updatedNested = { ...nested, a: { ...nested.a, b: 2 } };
```

For deep or complex state, consider Immer or similar to keep update logic readable while staying immutable.

[← Back to SKILL](../SKILL.md)
