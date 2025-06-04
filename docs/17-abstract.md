# Abstract Class Summary

## Abstract Class Concept
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

## Abstract Methods
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

## Abstract Class Rules
- Cannot create instance of abstract class
- Class must be abstract if it has abstract methods
- Abstract class can have concrete methods
- Abstract class can have fields
- Can have constructors (called by subclasses)

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
- Keep abstract classes focused and cohesive
- Document expected behavior of abstract methods
- Consider interfaces for pure abstractions
- Use meaningful names for abstract classes
- Provide default implementations when possible
