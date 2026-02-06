---
name: design-patterns-ts
description: TypeScript design patterns implementation guide. Use when: (1) User asks about design patterns, (2) Code needs restructuring for maintainability, (3) Implementing factories, observers, strategies, decorators, (4) User mentions pattern names like "singleton", "factory", "adapter", "observer", etc.
---

# Design Patterns (TypeScript)

Apply classic design patterns in TypeScript/JavaScript. Load the relevant reference file for full implementations.

## Pattern selection

| Problem | Pattern | Reference |
|--------|---------|-----------|
| Create objects without exposing instantiation logic | Simple Factory | [references/creational/simple-factory.md](references/creational/simple-factory.md) |
| Delegate object creation to subclasses | Factory Method | [references/creational/factory-method.md](references/creational/factory-method.md) |
| Create families of related objects | Abstract Factory | [references/creational/abstract-factory.md](references/creational/abstract-factory.md) |
| Build complex objects step-by-step | Builder | [references/creational/builder.md](references/creational/builder.md) |
| Clone existing objects instead of creating from scratch | Prototype | [references/creational/prototype.md](references/creational/prototype.md) |
| Ensure single instance of a class | Singleton | [references/creational/singleton.md](references/creational/singleton.md) |
| Make incompatible interfaces work together | Adapter | [references/structural/adapter.md](references/structural/adapter.md) |
| Decouple abstraction from implementation | Bridge | [references/structural/bridge.md](references/structural/bridge.md) |
| Treat individual objects and compositions uniformly | Composite | [references/structural/composite.md](references/structural/composite.md) |
| Add behavior to objects at runtime | Decorator | [references/structural/decorator.md](references/structural/decorator.md) |
| Simplify a complex subsystem with one interface | Facade | [references/structural/facade.md](references/structural/facade.md) |
| Share state across many similar objects | Flyweight | [references/structural/flyweight.md](references/structural/flyweight.md) |
| Control access to an object (lazy, cache, guard) | Proxy | [references/structural/proxy.md](references/structural/proxy.md) |
| Pass request along a chain of handlers | Chain of Responsibility | [references/behavioral/chain-of-responsibility.md](references/behavioral/chain-of-responsibility.md) |
| Encapsulate actions as objects (undo/redo) | Command | [references/behavioral/command.md](references/behavioral/command.md) |
| Traverse collections without exposing structure | Iterator | [references/behavioral/iterator.md](references/behavioral/iterator.md) |
| Centralize communication between objects | Mediator | [references/behavioral/mediator.md](references/behavioral/mediator.md) |
| Capture and restore object state (undo) | Memento | [references/behavioral/memento.md](references/behavioral/memento.md) |
| Notify dependents when state changes | Observer | [references/behavioral/observer.md](references/behavioral/observer.md) |
| Add operations to object structure without changing it | Visitor | [references/behavioral/visitor.md](references/behavioral/visitor.md) |
| Swap algorithms at runtime | Strategy | [references/behavioral/strategy.md](references/behavioral/strategy.md) |
| Change behavior when internal state changes | State | [references/behavioral/state.md](references/behavioral/state.md) |
| Define algorithm skeleton, subclasses fill steps | Template Method | [references/behavioral/template-method.md](references/behavioral/template-method.md) |

## References by category

- **Creational** (object creation): [references/creational/](references/creational/) — Simple Factory, Factory Method, Abstract Factory, Builder, Prototype, Singleton
- **Structural** (object composition): [references/structural/](references/structural/) — Adapter, Bridge, Composite, Decorator, Facade, Flyweight, Proxy
- **Behavioral** (object interaction): [references/behavioral/](references/behavioral/) — Chain of Responsibility, Command, Iterator, Mediator, Memento, Observer, Visitor, Strategy, State, Template Method

Load the specific pattern file when implementing or explaining that pattern.

## Anti-patterns to avoid

- Do not force a pattern when a simple function or object suffices.
- Prefer composition over inheritance where it fits (Bridge, Strategy, Decorator).
- Avoid overusing Singleton (global state, harder testing); consider dependency injection.
- Do not add patterns to "find" problems; use them to solve existing complexity.
