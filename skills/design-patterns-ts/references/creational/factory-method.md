# Factory Method

## Real-world example

A hiring manager can't interview for every position. Based on the job opening, she delegates the interview steps to different people (e.g. developer interviewer, marketing interviewer).

## In plain words

Factory Method delegates the instantiation logic to child classes.

## Wikipedia

> In class-based programming, the factory method pattern is a creational pattern that uses factory methods to deal with the problem of creating objects without having to specify the exact class of the object that will be created. This is done by creating objects by calling a factory method—either specified in an interface and implemented by child classes, or implemented in a base class and optionally overridden by derived classes—rather than by calling a constructor.

## TypeScript example

```typescript
interface Interviewer {
  askQuestions(): void;
}

class Developer implements Interviewer {
  askQuestions(): void {
    console.log('Asking about design patterns!');
  }
}

class CommunityExecutive implements Interviewer {
  askQuestions(): void {
    console.log('Asking about community building');
  }
}

abstract class HiringManager {
  abstract makeInterviewer(): Interviewer;

  takeInterview(): void {
    const interviewer = this.makeInterviewer();
    interviewer.askQuestions();
  }
}

class DevelopmentManager extends HiringManager {
  makeInterviewer(): Interviewer {
    return new Developer();
  }
}

class MarketingManager extends HiringManager {
  makeInterviewer(): Interviewer {
    return new CommunityExecutive();
  }
}

// Usage
const devManager = new DevelopmentManager();
devManager.takeInterview(); // Output: Asking about design patterns!

const marketingManager = new MarketingManager();
marketingManager.takeInterview(); // Output: Asking about community building.
```

## When to use?

Use when there is generic processing in a class but the required subclass is decided at runtime, or when the client doesn't know what exact subclass it might need.

[← Back to SKILL](../../SKILL.md)
