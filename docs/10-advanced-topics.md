# Advanced Topics

## Immutability

### Aliasing
- Multiple references pointing to the same object
- Changes through one reference affect all references
- Can lead to unexpected behavior
- Example:
  ```java
  List<Integer> list1 = new ArrayList<>();
  List<Integer> list2 = list1;  // alias created
  list1.add(1);  // affects both list1 and list2
  ```

### Immutability Concept
- Objects cannot be modified after creation
- All fields are final
- No mutator methods
- Returns new objects for modifications
- Example:
  ```java
  final class Point {
    private final double x;
    private final double y;
    
    public Point(double x, double y) {
      this.x = x;
      this.y = y;
    }
    
    public Point moveTo(double newX, double newY) {
      return new Point(newX, newY);  // returns new instance
    }
  }
  ```

### Benefits of Immutability
1. Thread Safety:
     - Safe for concurrent access
     - No synchronization needed

2. Easier Reasoning:
     - No state changes to track
     - Predictable behavior

3. Security:
     - Cannot be modified maliciously
     - Safe to share references

### Creating Immutable Classes
1. Make class final
2. Make fields private and final
3. No setter methods
4. Return new instances for modifications
5. Protect mutable fields

## Composition

### Composition Concept
- Building complex classes using simpler classes
- Models "HAS-A" relationship between classes
- Example:
  ```java
  class Circle {
    private Point c;   // Circle HAS-A Point
    private double r;
  }
  ```

### Benefits of Composition
- Builds layers of abstraction
- Encapsulates implementation details
- Makes code more modular
- Allows reuse of existing classes
- Simplifies complex class implementations

### Example of Composition
```java
// Building up from Point to Circle to Cylinder
class Point {
  private double x;
  private double y;
}

class Circle {
  private Point center;
  private double radius;
}

class Cylinder {
  private Circle base;
  private double height;
}
```

### Reference Sharing Issues
- Objects can share references to components
- Changes to shared components affect all objects
- Solutions:
  1. Avoid Sharing References
  2. Create Defensive Copies

## Java Streams

### Stream Concept
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

### Stream Operations
1. Intermediate Operations:
     - map: Transform elements
     - filter: Select elements
     - flatMap: One-to-many transformation
     - sorted: Sort elements
     - distinct: Remove duplicates

2. Terminal Operations:
     - collect: Accumulate elements
     - forEach: Process elements
     - reduce: Combine elements
     - count: Count elements

### Stream Characteristics
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
