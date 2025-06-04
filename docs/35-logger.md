# Logger (Loggable) Summary

## Loggable Concept
- Encapsulates value with logging information
- Maintains operation history
- Functional approach to logging
- Example:
  ```java
  class Loggable<T> {
    private final T value;
    private final String log;
    
    private Loggable(T value, String log) {
      this.value = value;
      this.log = log;
    }
  }
  ```

## Creating Loggable
- Static factory method
- Initialize with empty log
- Example:
  ```java
  public static <T> Loggable<T> of(T value) {
    return new Loggable<>(value, "");
  }
  ```

## Functional Operations
1. Map:
   ```java
   public <U> Loggable<U> map(Transformer<? super T, ? extends U> transformer) {
     return new Loggable<>(
       transformer.transform(this.value),
       this.log
     );
   }
   ```

2. FlatMap:
   ```java
   public <U> Loggable<U> flatMap(
       Transformer<? super T, ? extends Loggable<? extends U>> transformer) {
     Loggable<? extends U> newLoggable = transformer.transform(this.value);
     return new Loggable<>(
       newLoggable.value,
       this.log + newLoggable.log
     );
   }
   ```

## Usage Example
```java
Loggable<Integer> result = Loggable.of(4)
    .flatMap(x -> new Loggable<>(x + 1, "Added 1; "))
    .flatMap(x -> new Loggable<>(x * 2, "Multiplied by 2; "));
// value: 10
// log: "Added 1; Multiplied by 2; "
```

## Benefits
1. Side-effect Free:
     - Pure functional approach
     - No global state modification
     - Composable operations

2. Operation Tracking:
     - Maintains operation history
     - Debugging aid
     - Audit trail

3. Type Safety:
     - Generic implementation
     - Compile-time type checking
     - Safe operation chaining

## Best Practices
- Use meaningful log messages
- Chain operations functionally
- Keep logs concise
- Consider performance
- Handle null cases
- Document logging behavior
