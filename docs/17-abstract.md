# Abstract Class Summary

## Abstract Class Concept
- Share common behaviors for similar classes to inherit
- Model an IS-A relationship (`Circle` IS-A `Shape`)
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

> Notes:

> - Abstract class cannot be instantiated
  - Class must be abstract if it has abstract methods
  - Can contain abstract methods, concrete methods and fields
  - Can have no abstract methods
  - Can have constructors for subclasses to call

## Abstract Methods
- Methods without implementation
- Declared using `abstract` keyword

- Example:
  ```java
  abstract class Shape {
    abstract double getArea();  // subclasses must implement
  }
  ```

> Notes:

> - All abstract methods must be implemented by concrete subclasses
  - Abstract methods cannot be private or final
  - Subclasses must override all inherited abstract methods from that abstract class

## Concrete Classes
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

## When to Use Abstract Classes
- Define common characteristics of related classes
- Share code among several related classes
- Want to declare non-public members
- Need to provide default behavior
- Example:
  ```java
  abstract class Animal {
    private String name;
    
    public Animal(String name) {
      this.name = name;
    }
    
    abstract void makeSound();  // each animal sounds different
    
    void sleep() {             // common to all animals
      System.out.println("Zzz");
    }
  }
  ```

## Best Practices
- Use abstract classes to define base behavior
- Keep abstract classes focused and cohesive (i.e., all methods and fields should serve a clear purpose)
- Document expected behavior of abstract methods
- Consider interfaces for pure abstractions
- Use meaningful names for abstract classes
- Provide default implementations when possible
