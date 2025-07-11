# Immutability Summary

## Aliasing
- Multiple references pointing to the same object
- Changes through one reference affect all references
- Can lead to unexpected behavior
- Example:
  ```java
  List<Integer> list1 = new ArrayList<>();
  List<Integer> list2 = list1;  // alias created
  list1.add(1);  // affects both list1 and list2
  ```

- Common Issues:
  1. Unintended modifications
  2. Debugging complexity
  3. Concurrency challenges

## Immutability Concept
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

## Benefits of Immutability
1. Thread Safety:
     - Safe for concurrent access
     - No synchronization needed

2. Easier Reasoning:
     - No state changes to track
     - Predictable behavior

3. Security:
     - Cannot be modified maliciously
     - Safe to share references

4. Caching:
     - Can cache safely
     - No invalidation needed

## Creating Immutable Classes
1. Make class final
2. Make fields private and final
3. No setter methods
4. Return new instances for modifications
5. Protect mutable fields
- Example:
  ```java
  final class Circle {
    private final Point center;
    private final double radius;
    
    public Circle(Point center, double radius) {
      this.center = new Point(center.getX(), center.getY());  // defensive copy
      this.radius = radius;
    }
    
    public Point getCenter() {
      return new Point(center.getX(), center.getY());  // return copy
    }
  }
  ```

## Copy-on-Write Pattern
- Create new object for modifications
- Share unmodified objects
- Example:
  ```java
  public Circle resize(double factor) {
    return new Circle(this.center, this.radius * factor);
  }
  ```

## Best Practices
- Make classes immutable by default
- Use final liberally
- Create defensive copies
- Document immutability
- Consider performance implications
- Use factory methods for flexibility
