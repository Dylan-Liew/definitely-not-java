# Interface Summary

## Interface Concept
- Specify a contract to supply behaviors for classes to implement
- A collection of abstract methods
- Declared using `interface` keyword
- Example:
  ```java
  // Every class that needs getArea() can implement this interface
  interface GetAreable {
    double getArea();  // implicitly public abstract
  }
  

  // Abstract class
  abstract class Shape implements GetAreable {
    private int numOfAxesOfSymmetry;

    public boolean isSymmetric() {
      return numOfAxesOfSymmetry > 0;
    }
  } 

  // Concrete class
  class Flat extends RealEstate implements GetAreable {
    private String block;
        :

    @Override
    public double getArea() {
        :
    }
  }

  // Array with the interface constraints
  double findLargest(GetAreable[] array) { // Elements must already implemented GetAreable()
    double maxArea = 0;
    for (GetAreable curr : array) {
      double area = curr.getArea();
      if (area > maxArea) {
        maxArea = area;
      } 
    }
    return maxArea;
  }
  ```

> Notes:

> - All abstract methods in interfaces are `public abstract` implicitly
      - Cannot be `private` or `final`
  - Non-abstract methods in interfaces must be `default` or `static` or `private`
  - All fields in interfaces are `public static final` implicitly
      - A compile-time constant
      - Cannot be `private`
  - Interfaces cannot have constructors
  - Interfaces cannot be instantiated 

## Implementing Interfaces
- Classes use `implements` keyword
- Example:
  ```java
  class Circle implements GetAreable {
    @Override
    public double getArea() {
      return Math.PI * radius * radius;
    }
  }
  ```

> Notes:

> - A class can implement multiple interfaces
  - Must implement (@Override) all methods in interfaces
  - Interfaces can extend one or more interfaces
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

## Casting Using an Interface
- There is the possibility that a subclass could implement the interface.
- So compiler lets the cast through
- Example:
  ```java
  interface I {
  :
  }

  class A {
    :
  }

  class B implements I {
    :
  }
  ```
  ```java
  I i1 = new B(); // Compiles, widening type conversion
  I i2 = (I) new A(); // Compiles, but throws ClassCastException at run‑time because A doesn’t implement I
  A a = (A) new B(); // Does not compile
  B a = (B) new A(); // Does not compile
  ```
## Interface vs Abstract Class
- Interface:
    - Pure abstraction
    - Multiple implementation
    - No state (instance fields are not allowed)
    - All methods must be public
  
- Abstract Class:
    - Partial implementation
    - Single inheritance
    - Can have state
    - Abstract methods cannot be private only 
    - Concrete methods can be any visibility options


## Best Practices
- Use interfaces to define behavior
- Keep interfaces focused (single responsibility)
- Prefer interfaces over abstract classes
- Use meaningful method names
- Document expected behavior
- Consider providing default methods in Java 8+
