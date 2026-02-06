# Facade

## Real-world example

How do you turn on a computer? You hit the power button. That simple interface hides a lot of internal steps (power supply, BIOS, boot loader, etc.). The facade is that simple interface to a complex subsystem.

## In plain words

Facade provides a simplified interface to a complex subsystem.

## Wikipedia

> A facade is an object that provides a simplified interface to a larger body of code, such as a class library.

## TypeScript example

```typescript
class Computer {
  getElectricShock(): void {
    console.log('Ouch!');
  }
  makeSound(): void {
    console.log('Beep beep!');
  }
  showLoadingScreen(): void {
    console.log('Loading..');
  }
  bam(): void {
    console.log('Ready to be used!');
  }
  closeEverything(): void {
    console.log('Bup bup bup buzzzz!');
  }
  sooth(): void {
    console.log('Zzzzz');
  }
  pullCurrent(): void {
    console.log('Haaah!');
  }
}

class ComputerFacade {
  constructor(private computer: Computer) {}

  turnOn(): void {
    this.computer.getElectricShock();
    this.computer.makeSound();
    this.computer.showLoadingScreen();
    this.computer.bam();
  }

  turnOff(): void {
    this.computer.closeEverything();
    this.computer.pullCurrent();
    this.computer.sooth();
  }
}

// Usage
const computer = new ComputerFacade(new Computer());
computer.turnOn();  // Ouch! Beep beep! Loading.. Ready to be used!
computer.turnOff(); // Bup bup buzzz! Haah! Zzzzz
```

## When to use?

When you need a simple interface to a complex subsystem, or when you want to layer subsystems and expose only what clients need.

[← Back to SKILL](../../SKILL.md)
