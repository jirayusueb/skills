# Proxy

## Real-world example

An access card opens a door; you can also press a button that bypasses security. The door's main job is to open, but a proxy adds access control on top.

## In plain words

A proxy is a class that represents the functionality of another class. It can forward calls, add caching, or enforce access.

## Wikipedia

> A proxy is a class functioning as an interface to something else. A proxy can forward to the real object or provide additional logic (e.g. caching, precondition checks).

## TypeScript example

```typescript
interface Door {
  open(): void;
  close(): void;
}

class LabDoor implements Door {
  open(): void {
    console.log('Opening lab door');
  }
  close(): void {
    console.log('Closing the lab door');
  }
}

class SecuredDoor implements Door {
  constructor(private door: Door) {}

  open(password: string): void {
    if (this.authenticate(password)) {
      this.door.open();
    } else {
      console.log("Big no! It ain't possible.");
    }
  }

  private authenticate(password: string): boolean {
    return password === '$ecr@t';
  }

  close(): void {
    this.door.close();
  }
}

// Usage
const door = new SecuredDoor(new LabDoor());
door.open('invalid');     // Big no! It ain't possible.
door.open('$ecr@t');      // Opening lab door
door.close();            // Closing the lab door
```

## When to use?

When you need a placeholder or wrapper: lazy initialization, access control, logging, caching, or a local representative for a remote object.

[← Back to SKILL](../../SKILL.md)
