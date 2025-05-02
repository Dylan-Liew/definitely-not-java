# Interfaces and Abstract Classes

## Abstract Classes

### Abstract Class Concept
- Class that cannot be instantiated
- May contain abstract and concrete methods
- Declared using `abstract` keyword
- Example:
  ```java
  abstract class Shape {
    abstract double getArea();  // abstract method
    
    boolean isSymmetric() {     // concrete method
      return true;
    }
  }
  ```

### Abstract Methods
- Methods without implementation
- Must be implemented by concrete subclasses
- Declared using `abstract` keyword
- Cannot be private or final
- Example:
  ```java
  abstract class Shape {
    abstract double getArea();  // subclasses must implement
  }
  ```

### Concrete Classes
- Classes that implement all abstract methods
- Can be instantiated
- Must override all inherited abstract methods
- Example:
  ```java
  class Circle extends Shape {
    private double radius;
    
    @Override
    double getArea() {  // implements abstract method
      return Math.PI * radius * radius;
    }
  }
  ```

### When to Use Abstract Classes
- Define common characteristics of related classes
- Share code among several related classes
- Want to declare non-public members
- Need to provide default behavior

## Interfaces

### Interface Concept
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

### Implementing Interfaces
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

### Interface Characteristics
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

### Multiple Interface Implementation
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

| Feature | Interface | Abstract Class |
|---------|-----------|----------------|
| Multiple inheritance | Yes | No |
| Method implementation | Can have default methods | Can have concrete methods |
| Fields | Only constants | Any kind |
| Constructor | No | Yes |
| Access modifiers | All public | Any |
| Purpose | Define behavior | Partial implementation |
| Use case | When multiple types may implement the same behavior | When related classes share code |
