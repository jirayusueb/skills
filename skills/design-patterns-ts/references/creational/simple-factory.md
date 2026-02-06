# Simple Factory

## Real-world example

Consider building a house: you need doors. You can either build them yourself (wood, glue, nails, tools) or call a factory and get a built door delivered so you don't need to know how it's made.

## In plain words

Simple factory generates an instance for the client without exposing any instantiation logic.

## Wikipedia

> In object-oriented programming (OOP), a factory is an object for creating other objects – formally a factory is a function or method that returns objects of a varying prototype or class from some method call, which is assumed to be "new".

## TypeScript example

```typescript
interface Door {
  getWidth(): number;
  getHeight(): number;
}

class WoodenDoor implements Door {
  constructor(
    private width: number,
    private height: number
  ) {}

  getWidth(): number {
    return this.width;
  }

  getHeight(): number {
    return this.height;
  }
}

class DoorFactory {
  static makeDoor(width: number, height: number): Door {
    return new WoodenDoor(width, height);
  }
}

// Usage
const door = DoorFactory.makeDoor(100, 200);
console.log(`Width: ${door.getWidth()}`);
console.log(`Height: ${door.getHeight()}`);

const door2 = DoorFactory.makeDoor(50, 100);
```

## When to use?

When creating an object is not just a few assignments and involves some logic, put it in a dedicated factory instead of repeating the same code everywhere.

[← Back to SKILL](../../SKILL.md)
