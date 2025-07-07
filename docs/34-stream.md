# Java Stream Summary

## Stream Concept
- Sequence of elements
- Supports sequential/parallel operations
- Lazy evaluation
- Example:
  ```java
  Stream<String> stream = Stream.of("a", "b", "c");
  List<String> result = stream
    .map(String::toUpperCase)
    .collect(Collectors.toList());
  ```

## Creating Streams
1. From Collection:
   ```java
   List<String> list = Arrays.asList("a", "b", "c");
   Stream<String> stream = list.stream();
   ```

2. Static Factory Methods:
   ```java
   Stream<Integer> stream1 = Stream.of(1, 2, 3);
   Stream<Integer> stream2 = Stream.iterate(0, n -> n + 1);
   Stream<String> stream3 = Stream.generate(() -> "hello");
   ```

## Stream Operations
1. Intermediate Operations:
     - map: Transform elements
     - filter: Select elements
     - flatMap: One-to-many transformation
     - sorted: Sort elements
     - distinct: Remove duplicates
   ```java
   stream.filter(x -> x > 0)
        .map(x -> x * 2)
        .sorted()
   ```

2. Terminal Operations:
     - collect: Accumulate elements
     - forEach: Process elements
     - reduce: Combine elements
     - count: Count elements
   ```java
   int sum = stream.reduce(0, Integer::sum);
   long count = stream.count();
   ```

## Parallel Streams
- Automatic parallelization
- Use multiple threads
- Example:
  ```java
  list.parallelStream()
      .filter(x -> x > 0)
      .map(x -> x * 2)
      .collect(Collectors.toList());
  ```

## Stream Characteristics
- Single use only
- Lazy evaluation
- Non-interference required
- Stateless preferred
- Example:
  ```java
  Stream<String> stream = list.stream();
  stream.forEach(System.out::println);
  stream.forEach(System.out::println);  // IllegalStateException
  ```

## Best Practices
- Use streams for data processing
- Consider parallel streams for large datasets
- Avoid stateful operations
- Handle stream closure properly
- Use appropriate collectors
- Consider performance implications
