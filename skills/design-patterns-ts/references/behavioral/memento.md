# Memento

## Real-world example

A calculator saves the last calculation in memory (memento) so you can restore it with a button (caretaker). The calculator is the originator.

## In plain words

Memento captures and stores the current state of an object so it can be restored later in a smooth way.

## Wikipedia

> The memento pattern is a software design pattern that provides the ability to restore an object to its previous state (undo via rollback).

Often used to implement undo functionality.

## TypeScript example

```typescript
class EditorMemento {
  constructor(private content: string) {}
  getContent(): string {
    return this.content;
  }
}

class Editor {
  private content = '';

  type(words: string): void {
    this.content += ' ' + words;
  }

  getContent(): string {
    return this.content;
  }

  save(): EditorMemento {
    return new EditorMemento(this.content);
  }

  restore(memento: EditorMemento): void {
    this.content = memento.getContent();
  }
}

// Usage
const editor = new Editor();
editor.type('This is the first sentence.');
editor.type('This is second.');
const saved = editor.save();
editor.type('And this is third.');
console.log(editor.getContent());
editor.restore(saved);
console.log(editor.getContent()); // Back to "This is the first sentence. This is second."
```

## When to use?

When you need to capture and restore an object's state (undo/redo, snapshots, checkpoints).

[← Back to SKILL](../../SKILL.md)
