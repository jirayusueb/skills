# Decorator

## Real-world example

A car service shop offers multiple services. You pick a base service and add prices for extra services until you get the final cost. Each service type is a decorator.

## In plain words

Decorator lets you change the behavior of an object at runtime by wrapping it in an object of a decorator class.

## Wikipedia

> In object-oriented programming, the decorator pattern is a design pattern that allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class. It is often useful for adhering to the Single Responsibility Principle.

## TypeScript example

```typescript
interface Coffee {
  getCost(): number;
  getDescription(): string;
}

class SimpleCoffee implements Coffee {
  getCost(): number {
    return 10;
  }
  getDescription(): string {
    return 'Simple coffee';
  }
}

class MilkCoffee implements Coffee {
  constructor(private coffee: Coffee) {}
  getCost(): number {
    return this.coffee.getCost() + 2;
  }
  getDescription(): string {
    return `${this.coffee.getDescription()}, milk`;
  }
}

class WhipCoffee implements Coffee {
  constructor(private coffee: Coffee) {}
  getCost(): number {
    return this.coffee.getCost() + 5;
  }
  getDescription(): string {
    return `${this.coffee.getDescription()}, whip`;
  }
}

class VanillaCoffee implements Coffee {
  constructor(private coffee: Coffee) {}
  getCost(): number {
    return this.coffee.getCost() + 3;
  }
  getDescription(): string {
    return `${this.coffee.getDescription()}, vanilla`;
  }
}

// Usage
let someCoffee: Coffee = new SimpleCoffee();
console.log(someCoffee.getCost(), someCoffee.getDescription());

someCoffee = new MilkCoffee(someCoffee);
console.log(someCoffee.getCost(), someCoffee.getDescription());

someCoffee = new WhipCoffee(someCoffee);
console.log(someCoffee.getCost(), someCoffee.getDescription());

someCoffee = new VanillaCoffee(someCoffee);
console.log(someCoffee.getCost(), someCoffee.getDescription());
// 20, "Simple coffee, milk, whip, vanilla"
```

## When to use?

When you need to add responsibilities to individual objects dynamically without subclassing, or when extension by subclassing is impractical.

[← Back to SKILL](../../SKILL.md)
