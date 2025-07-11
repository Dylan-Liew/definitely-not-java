# Parallel Streams Summary

## Parallel Processing Concept
- Concurrent execution of tasks
- Uses multiple threads/cores
- Automatic work distribution
- Example:
  ```java
  List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
  numbers.parallelStream()
         .map(x -> x * 2)
         .collect(Collectors.toList());
  ```

## Creating Parallel Streams
1. From Collection:
   ```java
   // Method 1
   list.parallelStream()
   
   // Method 2
   list.stream().parallel()
   ```

2. From Arrays:
   ```java
   Arrays.stream(array).parallel()
   ```

## Parallel Stream Operations
1. Stateless Operations (Safe):
     - map
     - filter
     - flatMap
   ```java
   stream.parallel()
         .filter(x -> x > 0)
         .map(x -> x * 2)
   ```

2. Stateful Operations (Careful):
     - sorted
     - distinct
     - limit
   ```java
   stream.parallel()
         .sorted()      // may impact performance
         .distinct()    // requires coordination
   ```

## Performance Considerations
1. When to Use:
     - Large data sets
     - Computationally intensive
     - Independent operations
     - Multiple cores available

2. When to Avoid:
     - Small data sets
     - IO-bound operations
     - Operations with dependencies
     - Single core systems

## Thread Safety
1. Safe Operations:
   ```java
   // Thread-safe reduction
   int sum = numbers.parallelStream()
                   .reduce(0, Integer::sum);
   ```

2. Unsafe Operations:
   ```java
   // Not thread-safe
   List<Integer> list = new ArrayList<>();
   stream.parallel()
         .forEach(list::add);  // Don't do this!
   ```

## Best Practices
- Use thread-safe collections
- Avoid stateful operations
- Consider ordering requirements
- Test performance gains
- Handle exceptions properly
- Use appropriate collectors
- Example:
  ```java
  // Good practice
  List<Integer> result = numbers.parallelStream()
      .map(x -> expensiveOperation(x))
      .collect(Collectors.toList());
