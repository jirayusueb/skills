# Prototype

## Real-world example

Remember Dolly the sheep? It was cloned. The key idea is creating copies from an existing instance.

## In plain words

Create an object based on an existing object through cloning.

## Wikipedia

> The prototype pattern is a creational design pattern in software development. It is used when the type of objects to create is determined by a prototypical instance, which is cloned to produce new objects.

You create a copy of an existing object and modify it instead of building from scratch.

## TypeScript example

```typescript
class Sheep {
  constructor(
    public name: string,
    public category = 'Mountain Sheep'
  ) {}

  setName(name: string): void {
    this.name = name;
  }

  getName(): string {
    return this.name;
  }

  setCategory(category: string): void {
    this.category = category;
  }

  getCategory(): string {
    return this.category;
  }
}

// Usage: clone and modify
const original = new Sheep('Jolly');
console.log(original.getName());     // Jolly
console.log(original.getCategory()); // Mountain Sheep

const cloned = Object.create(Object.getPrototypeOf(original));
Object.assign(cloned, original);
cloned.setName('Dolly');
console.log(cloned.getName());     // Dolly
console.log(cloned.getCategory()); // Mountain Sheep

// Alternative with structuredClone (deep clone, modern runtimes)
const cloned2 = structuredClone(original);
cloned2.setName('Dolly');
```

## When to use?

When an object is similar to an existing one, or when creation would be more expensive than cloning.

[← Back to SKILL](../../SKILL.md)
