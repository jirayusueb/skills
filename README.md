# Design Patterns for Humans (TypeScript)

Ultra-simplified explanations of design patterns with TypeScript examples. Based on [design-patterns-for-humans](https://github.com/kamranahmedse/design-patterns-for-humans).

## Install as a skill

Use the bundled skills so an AI assistant can recommend and implement these patterns in your codebase:

```bash
# Design patterns (GoF)
npx skills add https://github.com/jirayusub/skills --skill design-patterns-ts

# Functional programming in TypeScript
npx skills add https://github.com/jirayusub/skills --skill functional-programming-ts
```

## What are design patterns?

Design patterns are **solutions to recurring problems**—guidelines for tackling certain problems in certain situations. They are not plug-in libraries; they are templates for how to solve a problem in many contexts.

> In software engineering, a software design pattern is a general reusable solution to a commonly occurring problem within a given context in software design. It is not a finished design that can be transformed directly into source or machine code.
> — Wikipedia

### Be careful

- Design patterns are not a silver bullet.
- Do not force them; misuse leads to unnecessary complexity.
- Patterns solve problems; they don’t exist to create problems. Don’t overthink.
- Used in the right place, they help; used wrongly, they complicate code.

## Types of design patterns

| Creational                 | Structural             | Behavioral                                       |
| -------------------------- | ---------------------- | ------------------------------------------------ |
| How to instantiate objects | How to compose objects | How objects interact and assign responsibilities |

## Table of contents

### Creational

| Pattern                                                                                 | Description                                               |
| --------------------------------------------------------------------------------------- | --------------------------------------------------------- |
| [Simple Factory](skills/design-patterns-ts/references/creational/simple-factory.md)     | Generate an instance without exposing instantiation logic |
| [Factory Method](skills/design-patterns-ts/references/creational/factory-method.md)     | Delegate instantiation to subclasses                      |
| [Abstract Factory](skills/design-patterns-ts/references/creational/abstract-factory.md) | Factory of related factories                              |
| [Builder](skills/design-patterns-ts/references/creational/builder.md)                   | Step-by-step object construction                          |
| [Prototype](skills/design-patterns-ts/references/creational/prototype.md)               | Create objects by cloning                                 |
| [Singleton](skills/design-patterns-ts/references/creational/singleton.md)               | Single instance of a class                                |

### Structural

| Pattern                                                                   | Description                                   |
| ------------------------------------------------------------------------- | --------------------------------------------- |
| [Adapter](skills/design-patterns-ts/references/structural/adapter.md)     | Make incompatible interfaces work together    |
| [Bridge](skills/design-patterns-ts/references/structural/bridge.md)       | Decouple abstraction from implementation      |
| [Composite](skills/design-patterns-ts/references/structural/composite.md) | Treat individuals and compositions uniformly  |
| [Decorator](skills/design-patterns-ts/references/structural/decorator.md) | Add behavior at runtime by wrapping           |
| [Facade](skills/design-patterns-ts/references/structural/facade.md)       | Simple interface to a complex subsystem       |
| [Flyweight](skills/design-patterns-ts/references/structural/flyweight.md) | Share state across many similar objects       |
| [Proxy](skills/design-patterns-ts/references/structural/proxy.md)         | Represent or control access to another object |

### Behavioral

| Pattern                                                                                               | Description                                          |
| ----------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| [Chain of Responsibility](skills/design-patterns-ts/references/behavioral/chain-of-responsibility.md) | Pass request along a chain of handlers               |
| [Command](skills/design-patterns-ts/references/behavioral/command.md)                                 | Encapsulate actions as objects                       |
| [Iterator](skills/design-patterns-ts/references/behavioral/iterator.md)                               | Traverse a collection without exposing structure     |
| [Mediator](skills/design-patterns-ts/references/behavioral/mediator.md)                               | Centralize communication between objects             |
| [Memento](skills/design-patterns-ts/references/behavioral/memento.md)                                 | Capture and restore object state                     |
| [Observer](skills/design-patterns-ts/references/behavioral/observer.md)                               | Notify dependents when state changes                 |
| [Visitor](skills/design-patterns-ts/references/behavioral/visitor.md)                                 | Add operations without changing structure            |
| [Strategy](skills/design-patterns-ts/references/behavioral/strategy.md)                               | Swap algorithms at runtime                           |
| [State](skills/design-patterns-ts/references/behavioral/state.md)                                     | Change behavior when state changes                   |
| [Template Method](skills/design-patterns-ts/references/behavioral/template-method.md)                 | Algorithm skeleton with steps deferred to subclasses |

## License

CC BY 4.0
