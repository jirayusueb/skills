# State

## Real-world example

In a drawing app you choose the paint brush. The brush behavior changes with the selected color: red draws red, blue draws blue. The brush's behavior depends on its current state.

## In plain words

State lets you change the behavior of a class when its internal state changes.

## Wikipedia

> The state pattern is a behavioral software design pattern that implements a state machine in an object-oriented way. Each state is implemented as a derived class of the state pattern interface, and state transitions are invoked via methods defined by the pattern's superclass. It can be interpreted as a strategy pattern that switches strategy through invocations of methods on the pattern's interface.

## TypeScript example

```typescript
interface PhoneState {
  pickUp(): PhoneState;
  hangUp(): PhoneState;
  dial(): PhoneState;
}

class PhoneStateIdle implements PhoneState {
  pickUp(): PhoneState {
    return new PhoneStatePickedUp();
  }
  hangUp(): PhoneState {
    throw new Error('already idle');
  }
  dial(): PhoneState {
    throw new Error('unable to dial in idle state');
  }
}

class PhoneStatePickedUp implements PhoneState {
  pickUp(): PhoneState {
    throw new Error('already picked up');
  }
  hangUp(): PhoneState {
    return new PhoneStateIdle();
  }
  dial(): PhoneState {
    return new PhoneStateCalling();
  }
}

class PhoneStateCalling implements PhoneState {
  pickUp(): PhoneState {
    throw new Error('already picked up');
  }
  hangUp(): PhoneState {
    return new PhoneStateIdle();
  }
  dial(): PhoneState {
    throw new Error('already dialing');
  }
}

class Phone {
  private state: PhoneState = new PhoneStateIdle();

  pickUp(): void {
    this.state = this.state.pickUp();
  }
  hangUp(): void {
    this.state = this.state.hangUp();
  }
  dial(): void {
    this.state = this.state.dial();
  }
}

// Usage
const phone = new Phone();
phone.pickUp();
phone.dial();
```

## When to use?

When an object's behavior depends on its state and you have many conditionals over that state (state machines, workflows, UI modes).

[← Back to SKILL](../../SKILL.md)
