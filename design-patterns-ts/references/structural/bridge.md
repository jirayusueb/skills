# Bridge

## Real-world example

You have a website with different pages and want to let users change the theme. Instead of duplicating each page for each theme, you have separate theme objects and compose them with pages. Bridge lets abstraction and implementation vary independently.

## In plain words

Bridge prefers composition over inheritance. Implementation details live in a separate hierarchy from the abstraction.

## Wikipedia

> The bridge pattern is a design pattern used in software engineering that is meant to "decouple an abstraction from its implementation so that the two can vary independently".

## TypeScript example

```typescript
interface Theme {
  getColor(): string;
}

class DarkTheme implements Theme {
  getColor(): string {
    return 'Dark Black';
  }
}

class LightTheme implements Theme {
  getColor(): string {
    return 'Off white';
  }
}

class AquaTheme implements Theme {
  getColor(): string {
    return 'Light blue';
  }
}

interface WebPage {
  getContent(): string;
}

class About implements WebPage {
  constructor(private theme: Theme) {}
  getContent(): string {
    return `About page in ${this.theme.getColor()}`;
  }
}

class Careers implements WebPage {
  constructor(private theme: Theme) {}
  getContent(): string {
    return `Careers page in ${this.theme.getColor()}`;
  }
}

// Usage
const darkTheme = new DarkTheme();
const about = new About(darkTheme);
const careers = new Careers(darkTheme);
console.log(about.getContent());   // About page in Dark Black
console.log(careers.getContent()); // Careers page in Dark Black
```

## When to use?

When you want to avoid a permanent binding between an abstraction and its implementation (e.g. themes, platforms, drivers).

[← Back to SKILL](../../SKILL.md)
