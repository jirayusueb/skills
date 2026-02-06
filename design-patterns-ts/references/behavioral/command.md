# Command

## Real-world example

You order food at a restaurant: you (client) ask the waiter (invoker) to bring food (command); the waiter forwards the request to the chef (receiver). Another example: you use a remote (invoker) to turn on the TV (receiver) via a "turn on" command.

## In plain words

Encapsulate actions in objects. The key idea is to decouple the client from the receiver.

## Wikipedia

> In object-oriented programming, the command pattern is a behavioral design pattern in which an object is used to encapsulate all information needed to perform an action or trigger an event at a later time. This information includes the method name, the object that owns the method, and values for the method parameters.

## TypeScript example

```typescript
// Receiver
class Bulb {
  turnOn(): void {
    console.log('Bulb has been lit');
  }
  turnOff(): void {
    console.log('Darkness!');
  }
}

interface Command {
  execute(): void;
  undo(): void;
  redo(): void;
}

class TurnOn implements Command {
  constructor(private bulb: Bulb) {}
  execute(): void {
    this.bulb.turnOn();
  }
  undo(): void {
    this.bulb.turnOff();
  }
  redo(): void {
    this.execute();
  }
}

class TurnOff implements Command {
  constructor(private bulb: Bulb) {}
  execute(): void {
    this.bulb.turnOff();
  }
  undo(): void {
    this.bulb.turnOn();
  }
  redo(): void {
    this.execute();
  }
}

// Invoker
class RemoteControl {
  submit(command: Command): void {
    command.execute();
  }
}

// Usage
const bulb = new Bulb();
const turnOn = new TurnOn(bulb);
const turnOff = new TurnOff(bulb);
const remote = new RemoteControl();
remote.submit(turnOn);  // Bulb has been lit!
remote.submit(turnOff); // Darkness!
```

## When to use?

When you need to parameterize objects by actions, queue or log requests, or support undo/redo (keep history of commands).

[← Back to SKILL](../../SKILL.md)
