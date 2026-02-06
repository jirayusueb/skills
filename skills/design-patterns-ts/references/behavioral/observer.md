# Observer

## Real-world example

Job seekers subscribe to a job posting site and get notified when there is a matching job. The site is the subject; the seekers are observers.

## In plain words

Define a one-to-many dependency so that when one object changes state, all its dependents are notified.

## Wikipedia

> The observer pattern is a software design pattern in which an object, called the subject, maintains a list of its dependents, called observers, and notifies them automatically of any state changes, usually by calling one of their methods.

## TypeScript example

```typescript
class JobPost {
  constructor(public title: string) {}
}

interface Observer {
  onJobPosted(job: JobPost): void;
}

class JobSeeker implements Observer {
  constructor(private name: string) {}

  onJobPosted(job: JobPost): void {
    console.log(`Hi ${this.name}! New job posted: ${job.title}`);
  }
}

class EmploymentAgency {
  private observers: Observer[] = [];

  attach(observer: Observer): void {
    this.observers.push(observer);
  }

  addJob(jobPosting: JobPost): void {
    this.observers.forEach(observer => observer.onJobPosted(jobPosting));
  }
}

// Usage
const johnDoe = new JobSeeker('John Doe');
const janeDoe = new JobSeeker('Jane Doe');
const jobPostings = new EmploymentAgency();
jobPostings.attach(johnDoe);
jobPostings.attach(janeDoe);
jobPostings.addJob(new JobPost('Software Engineer'));
// Hi John Doe! New job posted: Software Engineer
// Hi Jane Doe! New job posted: Software Engineer
```

## When to use?

When a change to one object requires changing others and you don't know how many objects need to be updated (event systems, MVC, reactive UIs).

[← Back to SKILL](../../SKILL.md)
