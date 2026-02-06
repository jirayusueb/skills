# Strategy

## Real-world example

You implemented bubble sort but data grew and it became slow. You added quick sort for large datasets, but quick sort was slow for small ones. You use a strategy: bubble sort for small datasets, quick sort for large.

## In plain words

Strategy lets you switch the algorithm or strategy based on the situation.

## Wikipedia

> In computer programming, the strategy pattern (also known as the policy pattern) is a behavioural software design pattern that enables an algorithm's behavior to be selected at runtime.

## TypeScript example

```typescript
interface SortStrategy {
  sort(dataset: number[]): number[];
}

class BubbleSortStrategy implements SortStrategy {
  sort(dataset: number[]): number[] {
    console.log('Sorting using bubble sort');
    return [...dataset].sort((a, b) => a - b);
  }
}

class QuickSortStrategy implements SortStrategy {
  sort(dataset: number[]): number[] {
    console.log('Sorting using quick sort');
    return [...dataset].sort((a, b) => a - b);
  }
}

class Sorter {
  constructor(
    private sorterSmall: SortStrategy,
    private sorterBig: SortStrategy
  ) {}

  sort(dataset: number[]): number[] {
    if (dataset.length > 5) {
      return this.sorterBig.sort(dataset);
    }
    return this.sorterSmall.sort(dataset);
  }
}

// Usage
const smallDataset = [1, 3, 4, 2];
const bigDataset = [1, 4, 3, 2, 8, 10, 5, 6, 9, 7];
const sorter = new Sorter(new BubbleSortStrategy(), new QuickSortStrategy());
sorter.sort(smallDataset);  // Sorting using bubble sort
sorter.sort(bigDataset);    // Sorting using quick sort
```

## When to use?

When you have multiple algorithms for the same task and want to choose one at runtime (sorting, compression, validation strategies).

[← Back to SKILL](../../SKILL.md)
