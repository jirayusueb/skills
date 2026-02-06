# Builder

## Real-world example

Imagine ordering a "Big Hardee" and getting it without questions (simple factory). For a customized Subway deal you choose bread, sauces, cheese, etc. Builder fits the latter: multiple steps and options.

## In plain words

Builder lets you create different flavors of an object while avoiding constructor pollution. Useful when there are several flavors or many steps in creation.

## Wikipedia

> The builder pattern is an object creation software design pattern with the intentions of finding a solution to the telescoping constructor anti-pattern.

Telescoping constructor: too many optional parameters in one constructor, making it hard to read and maintain.

## TypeScript example

```typescript
class Burger {
  constructor(
    public size: number,
    public cheese = false,
    public pepperoni = false,
    public lettuce = false,
    public tomato = false
  ) {}
}

class BurgerBuilder {
  public cheese = false;
  public pepperoni = false;
  public lettuce = false;
  public tomato = false;

  constructor(public size: number) {}

  addPepperoni(): this {
    this.pepperoni = true;
    return this;
  }

  addLettuce(): this {
    this.lettuce = true;
    return this;
  }

  addCheese(): this {
    this.cheese = true;
    return this;
  }

  addTomato(): this {
    this.tomato = true;
    return this;
  }

  build(): Burger {
    return new Burger(
      this.size,
      this.cheese,
      this.pepperoni,
      this.lettuce,
      this.tomato
    );
  }
}

// Usage
const burger = new BurgerBuilder(14)
  .addPepperoni()
  .addLettuce()
  .addTomato()
  .build();
```

## When to use?

When an object has several flavors or creation is a multi-step process. Factory is for one-step creation; Builder is for multi-step.

[← Back to SKILL](../../SKILL.md)
