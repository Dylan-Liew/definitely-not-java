# Lazy Evaluation Summary

## Lazy Evaluation Concept
- Delays computation until needed
- Avoids unnecessary calculations
- Can improve performance
- Example:
  ```java
  class Lazy<T> {
    private T value;
    private boolean evaluated;
    private Producer<T> producer;
    
    public Lazy(Producer<T> producer) {
      this.producer = producer;
      this.evaluated = false;
    }
  }
  ```

## Memoization
- Caches computed results
- Computes only once
- Reuses cached value
- Example:
  ```java
  public T get() {
    if (!evaluated) {
      value = producer.produce();
      evaluated = true;
    }
    return value;
  }
  ```

## Lazy Operations
- map: Transform value lazily
- flatMap: Chain lazy computations
- Example:
  ```java
  Lazy<Integer> lazyNum = new Lazy<>(() -> expensiveComputation());
  Lazy<String> lazyStr = lazyNum.map(n -> n.toString());
  ```

## Benefits of Lazy Evaluation
1. Performance:
     - Avoids unnecessary computations
     - Saves resources

2. Infinite Structures:
     - Can represent infinite sequences
     - Only computes needed values

3. Short-circuit Evaluation:
     - Stops when result is determined
     - Avoids redundant work

## Practical Applications
- Logging systems
- Configuration loading
- Database queries
- Example:
  ```java
  Lazy<String> log = new Lazy<>(() -> 
    "User " + expensiveUserLookup() + " logged in");
  
  if (debugEnabled) {
    System.out.println(log.get());  // only computed if needed
  }
  ```

## Best Practices
- Use for expensive computations
- Implement memoization
- Consider thread safety
- Document lazy behavior
- Handle exceptions properly
- Test both lazy and eager paths
