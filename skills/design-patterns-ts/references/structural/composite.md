# Composite

## Real-world example

An organization is composed of employees. Each employee has a salary, responsibilities, may report to someone, and may have subordinates. You want to treat individuals and groups uniformly (e.g. total salary of a department).

## In plain words

Composite lets clients treat individual objects and compositions of objects in a uniform way.

## Wikipedia

> The composite pattern describes that a group of objects is to be treated in the same way as a single instance of an object. The intent of a composite is to "compose" objects into tree structures to represent part-whole hierarchies. Implementing the composite pattern lets clients treat individual objects and compositions uniformly.

## TypeScript example

```typescript
interface Employee {
  getName(): string;
  setSalary(salary: number): void;
  getSalary(): number;
  getRoles(): string[];
}

class Developer implements Employee {
  constructor(
    private name: string,
    private salary: number
  ) {}

  getName(): string {
    return this.name;
  }
  setSalary(salary: number): void {
    this.salary = salary;
  }
  getSalary(): number {
    return this.salary;
  }
  getRoles(): string[] {
    return [];
  }
}

class Designer implements Employee {
  constructor(
    private name: string,
    private salary: number
  ) {}

  getName(): string {
    return this.name;
  }
  setSalary(salary: number): void {
    this.salary = salary;
  }
  getSalary(): number {
    return this.salary;
  }
  getRoles(): string[] {
    return [];
  }
}

class Organization {
  private employees: Employee[] = [];

  addEmployee(employee: Employee): void {
    this.employees.push(employee);
  }

  getNetSalaries(): number {
    return this.employees.reduce((sum, e) => sum + e.getSalary(), 0);
  }
}

// Usage
const john = new Developer('John Doe', 12000);
const jane = new Designer('Jane Doe', 15000);
const organization = new Organization();
organization.addEmployee(john);
organization.addEmployee(jane);
console.log('Net salaries:', organization.getNetSalaries()); // 27000
```

## When to use?

When you have tree structures and want to treat leaves and composites the same (menus, file systems, org charts).

[← Back to SKILL](../../SKILL.md)
