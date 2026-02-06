# Chain of Responsibility

## Real-world example

You have three payment methods (A, B, C) with different balances; preference is A then B then C. You try to buy something for 210 USD. Account A is checked first; if it can't pay, the request goes to B, then C, until one handles it.

## In plain words

Build a chain of objects. A request enters at one end and moves from object to object until a suitable handler is found.

## Wikipedia

> In object-oriented design, the chain-of-responsibility pattern is a design pattern consisting of a source of command objects and a series of processing objects. Each processing object contains logic that defines which command objects it can handle; the rest are passed to the next processing object in the chain.

## TypeScript example

```typescript
abstract class Account {
  protected successor?: Account;
  protected balance: number;

  constructor(balance: number) {
    this.balance = balance;
  }

  setNext(account: Account): void {
    this.successor = account;
  }

  pay(amountToPay: number): void {
    if (this.canPay(amountToPay)) {
      console.log(`Paid ${amountToPay} using ${this.constructor.name}`);
    } else if (this.successor) {
      console.log(`Cannot pay using ${this.constructor.name}. Proceeding ..`);
      this.successor.pay(amountToPay);
    } else {
      throw new Error('None of the accounts have enough balance');
    }
  }

  canPay(amount: number): boolean {
    return this.balance >= amount;
  }
}

class Bank extends Account {
  constructor(balance: number) {
    super(balance);
  }
}

class Paypal extends Account {
  constructor(balance: number) {
    super(balance);
  }
}

class Bitcoin extends Account {
  constructor(balance: number) {
    super(balance);
  }
}

// Usage: Bank -> Paypal -> Bitcoin
const bank = new Bank(100);
const paypal = new Paypal(200);
const bitcoin = new Bitcoin(300);
bank.setNext(paypal);
paypal.setNext(bitcoin);
bank.pay(259);
// Cannot pay using Bank. Proceeding ..
// Cannot pay using Paypal. Proceeding ..
// Paid 259 using Bitcoin
```

## When to use?

When more than one object may handle a request and the handler isn't known a priori (e.g. event bubbling, middleware pipelines).

[← Back to SKILL](../../SKILL.md)
