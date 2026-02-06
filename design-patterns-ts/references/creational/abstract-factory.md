# Abstract Factory

## Real-world example

Extending the door example: you might get a wooden door from a wooden door shop, an iron door from an iron shop, or a PVC door from a relevant shop. You also need a fitting expert (carpenter for wooden, welder for iron). The doors and experts are related families.

## In plain words

Abstract Factory is a factory of factories: it groups individual but related/dependent factories together without specifying their concrete classes.

## Wikipedia

> The abstract factory pattern provides a way to encapsulate a group of individual factories that have a common theme without specifying their concrete classes.

## TypeScript example

```typescript
interface Door {
  getDescription(): void;
}

class WoodenDoor implements Door {
  getDescription(): void {
    console.log('I am a wooden door');
  }
}

class IronDoor implements Door {
  getDescription(): void {
    console.log('I am an iron door');
  }
}

interface DoorFittingExpert {
  getDescription(): void;
}

class Welder implements DoorFittingExpert {
  getDescription(): void {
    console.log('I can only fit iron doors');
  }
}

class Carpenter implements DoorFittingExpert {
  getDescription(): void {
    console.log('I can only fit wooden doors');
  }
}

interface DoorFactory {
  makeDoor(): Door;
  makeFittingExpert(): DoorFittingExpert;
}

class WoodenDoorFactory implements DoorFactory {
  makeDoor(): Door {
    return new WoodenDoor();
  }
  makeFittingExpert(): DoorFittingExpert {
    return new Carpenter();
  }
}

class IronDoorFactory implements DoorFactory {
  makeDoor(): Door {
    return new IronDoor();
  }
  makeFittingExpert(): DoorFittingExpert {
    return new Welder();
  }
}

// Usage
const woodenFactory = new WoodenDoorFactory();
const door = woodenFactory.makeDoor();
const expert = woodenFactory.makeFittingExpert();
door.getDescription();   // I am a wooden door
expert.getDescription(); // I can only fit wooden doors

const ironFactory = new IronDoorFactory();
const door2 = ironFactory.makeDoor();
const expert2 = ironFactory.makeFittingExpert();
door2.getDescription();   // I am an iron door
expert2.getDescription(); // I can only fit iron doors
```

## When to use?

When there are interrelated dependencies with non-trivial creation logic (families of related products).

[← Back to SKILL](../../SKILL.md)
