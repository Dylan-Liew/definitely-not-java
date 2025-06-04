# Interface Summary

## Interface Concept
- Contract specifying behavior
- Collection of abstract methods
- Can have constants (public static final)
- Declared using `interface` keyword
- Example:
  ```java
  interface GetAreable {
    double getArea();  // implicitly public abstract
  }
  ```

## Implementing Interfaces
- Classes use `implements` keyword
- Can implement multiple interfaces
- Must implement all methods
- Example:
  ```java
  class Circle implements GetAreable {
    @Override
    public double getArea() {
      return Math.PI * radius * radius;
    }
  }
  ```

## Interface Characteristics
- All methods implicitly public abstract
- All fields implicitly public static final
- Cannot have constructor
- Cannot be instantiated
- Can extend multiple interfaces
- Example:
  ```java
  interface Drawable extends GetAreable {
    void draw();  // adds another abstract method
  }
  ```

## Multiple Interface Implementation
- Class can implement many interfaces
- Must implement all methods from all interfaces
- Example:
  ```java
  class Square implements GetAreable, Comparable<Square> {
    @Override
    public double getArea() { return side * side; }
    
    @Override
    public int compareTo(Square other) {
      return Double.compare(this.getArea(), other.getArea());
    }
  }
  ```

## Interface vs Abstract Class
- Interface:
    - Pure abstraction
    - Multiple implementation
    - No state
    - All methods public
  
- Abstract Class:
    - Partial implementation
    - Single inheritance
    - Can have state
    - Methods any visibility

## Best Practices
- Use interfaces to define behavior
- Keep interfaces focused (single responsibility)
- Prefer interfaces over abstract classes
- Use meaningful method names
- Document expected behavior
- Consider providing default methods in Java 8+
