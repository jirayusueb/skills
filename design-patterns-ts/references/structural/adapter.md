# Adapter

## Real-world example

You have pictures on a memory card and need to transfer them to a computer. You use a card reader (adapter) compatible with your computer's ports. Another example: a power adapter makes a three-legged plug work with a two-prong outlet.

## In plain words

Adapter wraps an otherwise incompatible object so it becomes compatible with another interface.

## Wikipedia

> In software engineering, the adapter pattern is a software design pattern that allows the interface of an existing class to be used as another interface. It is often used to make existing classes work with others without modifying their source code.

## TypeScript example

```typescript
interface Lion {
  roar(): void;
}

class AfricanLion implements Lion {
  roar(): void {}
}

class AsianLion implements Lion {
  roar(): void {}
}

class Hunter {
  hunt(lion: Lion): void {
    lion.roar();
  }
}

// Incompatible: WildDog has bark(), not roar()
class WildDog {
  bark(): void {}
}

// Adapter makes WildDog work with Hunter
class WildDogAdapter implements Lion {
  constructor(private dog: WildDog) {}

  roar(): void {
    this.dog.bark();
  }
}

// Usage
const wildDog = new WildDog();
const wildDogAdapter = new WildDogAdapter(wildDog);
const hunter = new Hunter();
hunter.hunt(wildDogAdapter);
```

## When to use?

When you need to use an existing class whose interface doesn't match what the client expects, and you can't or don't want to change the original class.

[← Back to SKILL](../../SKILL.md)
