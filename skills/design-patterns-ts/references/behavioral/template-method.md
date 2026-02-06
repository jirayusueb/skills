# Template Method

## Real-world example

Building a house: prepare base, build walls, add roof, add other floors. The order is fixed (can't build roof before walls), but each step can be modified (e.g. walls of wood, polyester, or stone).

## In plain words

Template Method defines the skeleton of an algorithm but defers some steps to subclasses.

## Wikipedia

> In software engineering, the template method pattern is a behavioral design pattern that defines the program skeleton of an algorithm in an operation, deferring some steps to subclasses. It lets one redefine certain steps of an algorithm without changing the algorithm's structure.

## TypeScript example

```typescript
abstract class Builder {
  // Template method
  build(): void {
    this.test();
    this.lint();
    this.assemble();
    this.deploy();
  }

  abstract test(): void;
  abstract lint(): void;
  abstract assemble(): void;
  abstract deploy(): void;
}

class AndroidBuilder extends Builder {
  test(): void {
    console.log('Running android tests');
  }
  lint(): void {
    console.log('Linting the android code');
  }
  assemble(): void {
    console.log('Assembling the android build');
  }
  deploy(): void {
    console.log('Deploying android build to server');
  }
}

class IosBuilder extends Builder {
  test(): void {
    console.log('Running ios tests');
  }
  lint(): void {
    console.log('Linting the ios code');
  }
  assemble(): void {
    console.log('Assembling the ios build');
  }
  deploy(): void {
    console.log('Deploying ios build to server');
  }
}

// Usage
const androidBuilder = new AndroidBuilder();
androidBuilder.build();
// Running android tests
// Linting the android code
// Assembling the android build
// Deploying android build to server

const iosBuilder = new IosBuilder();
iosBuilder.build();
```

## When to use?

When you have an algorithm with invariant steps and steps that vary by subclass (build pipelines, document generation, test runners).

[← Back to SKILL](../../SKILL.md)
