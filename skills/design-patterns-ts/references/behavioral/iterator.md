# Iterator

## Real-world example

An old radio: you start on a channel and use next/previous to move through channels. Same idea for MP3 player or TV—they expose a way to iterate over channels, songs, or stations without exposing internal structure.

## In plain words

Iterator presents a way to access elements of a collection without exposing the underlying representation.

## Wikipedia

> In object-oriented programming, the iterator pattern is a design pattern in which an iterator is used to traverse a container and access the container's elements. The iterator pattern decouples algorithms from containers.

## TypeScript example

```typescript
class RadioStation {
  constructor(public frequency: number) {}
}

class StationList implements Iterable<RadioStation> {
  private stations: RadioStation[] = [];

  addStation(station: RadioStation): void {
    this.stations.push(station);
  }

  removeStation(toRemove: RadioStation): void {
    const freq = toRemove.frequency;
    this.stations = this.stations.filter(s => s.frequency !== freq);
  }

  [Symbol.iterator](): Iterator<RadioStation> {
    let index = 0;
    const stations = this.stations;
    return {
      next(): IteratorResult<RadioStation> {
        if (index < stations.length) {
          return { value: stations[index++], done: false };
        }
        return { value: undefined as unknown as RadioStation, done: true };
      },
    };
  }
}

// Usage
const stationList = new StationList();
stationList.addStation(new RadioStation(89));
stationList.addStation(new RadioStation(101));
stationList.addStation(new RadioStation(102));
stationList.addStation(new RadioStation(103.2));

for (const station of stationList) {
  console.log(station.frequency);
}
```

## When to use?

When you need to traverse a collection in a uniform way without exposing its internal structure, or when you want multiple traversal strategies over the same structure.

[← Back to SKILL](../../SKILL.md)
