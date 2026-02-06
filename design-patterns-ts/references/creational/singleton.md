# Singleton

## Real-world example

There can only be one president of a country at a time. The same president is used whenever duty calls.

## In plain words

Ensures that only one instance of a particular class ever exists.

## Wikipedia

> In software engineering, the singleton pattern is a software design pattern that restricts the instantiation of a class to one object. This is useful when exactly one object is needed to coordinate actions across the system.

Singleton is often considered an anti-pattern: it introduces global state, makes testing and mocking harder, and couples code. Use sparingly; prefer dependency injection where possible.

## TypeScript example

```typescript
class President {
  private static instance: President;

  private constructor() {
    // Hide the constructor
  }

  static getInstance(): President {
    if (!President.instance) {
      President.instance = new President();
    }
    return President.instance;
  }

  private static preventClone(): void {}
}

// Prevent cloning in runtime (TypeScript doesn't have __clone; document that cloning breaks singleton)
const president1 = President.getInstance();
const president2 = President.getInstance();
console.log(president1 === president2); // true
```

## When to use?

When exactly one instance must coordinate actions (e.g. config, connection pool). Prefer passing the instance (dependency injection) over global getInstance() where testability matters.

[← Back to SKILL](../../SKILL.md)
