# Interface Summary

## Interface Concept
- Specify a contract that specifies what methods a class must implement
- A collection of abstract methods
- Declared using `interface` keyword
- Example:
  ```java
  // Interface defining a contract for objects that have an area
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
  double findLargest(GetAreable[] array) {
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

## Multiple Interface Implementation
- Class can `implements` many interfaces
- Interfaces can `extends` one or more interfaces
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
- The compiler allows casting to an interface type because a subclass may implement that interface.
- However, if the actual object does not implement the interface, a `ClassCastException` will be thrown at runtime.
- Example:
  ```java
  interface I {
    // interface methods
  }

  class A {
    // class A implementation
  }

  class B implements I {
    // class B implementation
  }
  ```
  ```java
  I i1 = new B();           // Valid: B implements I, assigned to interface reference
  I i2 = (I) new A();       // Compiles, but throws ClassCastException at runtime (A does not implement I)
  A a = (A) new B();        // Compile-time error: incompatible types
  B b = (B) new A();        // Compile-time error: incompatible types
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
