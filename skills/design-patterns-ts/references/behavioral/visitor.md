# Visitor

## Real-world example

Someone visiting Dubai needs a visa to enter. After arrival they can visit any place without asking permission—just add places to the list and they can visit. Visitor lets you add new operations to object structures without modifying the structures.

## In plain words

Visitor lets you add further operations to objects without having to modify them.

## Wikipedia

> In object-oriented programming and software engineering, the visitor design pattern is a way of separating an algorithm from an object structure on which it operates. A practical result is the ability to add new operations to existing object structures without modifying those structures (open/closed principle).

## TypeScript example

```typescript
interface Animal {
  accept(operation: AnimalOperation): void;
}

interface AnimalOperation {
  visitMonkey(monkey: Monkey): void;
  visitLion(lion: Lion): void;
  visitDolphin(dolphin: Dolphin): void;
}

class Monkey implements Animal {
  shout(): void {
    console.log('Ooh oo aa aa!');
  }
  accept(operation: AnimalOperation): void {
    operation.visitMonkey(this);
  }
}

class Lion implements Animal {
  roar(): void {
    console.log('Roaaar!');
  }
  accept(operation: AnimalOperation): void {
    operation.visitLion(this);
  }
}

class Dolphin implements Animal {
  speak(): void {
    console.log('Tuut tuttu tuutt!');
  }
  accept(operation: AnimalOperation): void {
    operation.visitDolphin(this);
  }
}

class Speak implements AnimalOperation {
  visitMonkey(monkey: Monkey): void {
    monkey.shout();
  }
  visitLion(lion: Lion): void {
    lion.roar();
  }
  visitDolphin(dolphin: Dolphin): void {
    dolphin.speak();
  }
}

class Jump implements AnimalOperation {
  visitMonkey(): void {
    console.log('Jumped 20 feet high! on to the tree!');
  }
  visitLion(): void {
    console.log('Jumped 7 feet! Back on the ground!');
  }
  visitDolphin(): void {
    console.log('Walked on water a little and disappeared');
  }
}

// Usage
const monkey = new Monkey();
const lion = new Lion();
const dolphin = new Dolphin();
const speak = new Speak();
const jump = new Jump();
monkey.accept(speak);   // Ooh oo aa aa!
monkey.accept(jump);    // Jumped 20 feet high! ...
lion.accept(speak);     // Roaaar!
dolphin.accept(speak);  // Tuut tuttu tuutt!
```

## When to use?

When you have a stable object structure and want to add new operations without changing the classes (e.g. AST visitors, document exporters).

[← Back to SKILL](../../SKILL.md)
