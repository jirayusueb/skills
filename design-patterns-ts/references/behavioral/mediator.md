# Mediator

## Real-world example

When you call someone on your phone, a network provider sits between you and them; your conversation goes through it. The network provider is the mediator.

## In plain words

Mediator adds a third-party object (mediator) to control the interaction between two or more objects (colleagues). It reduces coupling because colleagues don't need to know each other's implementation.

## Wikipedia

> In software engineering, the mediator pattern defines an object that encapsulates how a set of objects interact. This pattern is considered to be a behavioral pattern due to the way it can alter the program's running behavior.

## TypeScript example

```typescript
interface ChatRoomMediator {
  showMessage(user: User, message: string): void;
}

class ChatRoom implements ChatRoomMediator {
  showMessage(user: User, message: string): void {
    const time = new Date().toLocaleString();
    const sender = user.getName();
    console.log(`${time} [${sender}]: ${message}`);
  }
}

class User {
  constructor(
    private name: string,
    private chatMediator: ChatRoomMediator
  ) {}

  getName(): string {
    return this.name;
  }

  send(message: string): void {
    this.chatMediator.showMessage(this, message);
  }
}

// Usage
const mediator = new ChatRoom();
const john = new User('John Doe', mediator);
const jane = new User('Jane Doe', mediator);
john.send('Hi there!');
jane.send('Hey!');
```

## When to use?

When many objects communicate in complex ways and you want to centralize that logic (e.g. chat rooms, form validation coordinating fields, dialog boxes).

[← Back to SKILL](../../SKILL.md)
