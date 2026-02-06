# Flyweight

## Real-world example

A tea stall often makes more than one cup of the same type and keeps the rest for other customers to save resources (e.g. gas). Flyweight is about sharing: reuse what is common across many objects.

## In plain words

Minimize memory usage or computational cost by sharing as much as possible with similar objects.

## Wikipedia

> A flyweight is an object that minimizes memory use by sharing as much data as possible with other similar objects; it is a way to use objects in large numbers when a simple repeated representation would use an unacceptable amount of memory.

## TypeScript example

```typescript
// Flyweight: shared, cached
class KarakTea {}

// Factory and cache
class TeaMaker {
  private availableTea: Record<string, KarakTea> = {};

  make(preference: string): KarakTea {
    if (!this.availableTea[preference]) {
      this.availableTea[preference] = new KarakTea();
    }
    return this.availableTea[preference];
  }
}

class TeaShop {
  private orders: Record<number, KarakTea> = {};

  constructor(private teaMaker: TeaMaker) {}

  takeOrder(teaType: string, table: number): void {
    this.orders[table] = this.teaMaker.make(teaType);
  }

  serve(): void {
    for (const [table, tea] of Object.entries(this.orders)) {
      console.log(`Serving tea to table# ${table}`);
    }
  }
}

// Usage
const teaMaker = new TeaMaker();
const shop = new TeaShop(teaMaker);
shop.takeOrder('less sugar', 1);
shop.takeOrder('more milk', 2);
shop.takeOrder('without sugar', 5);
shop.serve();
```

## When to use?

When you have many similar objects and can move shared state (intrinsic) into one place and keep only varying state (extrinsic) in the instances.

[← Back to SKILL](../../SKILL.md)
