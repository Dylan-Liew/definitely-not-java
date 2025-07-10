# Inheritance Summary

## Inheritance Concept
- Mechanism to extend existing code
- Models "IS-A" relationship between classes
- Uses `extends` keyword in Java
- Example:
  ```java
  class ColoredCircle extends Circle {
    private Color color;
  }
  ```

## Key Characteristics
- Subclass inherits:
    - Public fields from parent
    - Public methods from parent
- Private members remain inaccessible
- `super` keyword accesses parent members
- `super` keyword must be first statement in constructor
- Example:
  ```java
  class ColoredCircle extends Circle {
    public ColoredCircle(Point center, double radius, Color color) {
      super(center, radius);  // call parent constructor to initialise its centre and radius
      this.color = color;
    }
  }
  ```

## When to Use Inheritance
- Use when subclass IS-A superclass
- Subclass should be substitutable for superclass
- Example of proper use:
  ```java
  // Square IS-A Shape
  class Square extends Shape { }
  ```
- Example of improper use:
  ```java
  // Circle is not a Point
  class Circle extends Point { }
  ```

## Composition vs Inheritance
- Composition: HAS-A relationship
  ```java
  class Car {
    private Engine engine;  // Car HAS-A Engine
  }
  ```
- Inheritance: IS-A relationship
  ```java
  class Car extends Vehicle {  // Car IS-A Vehicle
  }
  ```

## Type Checking
- Superclass is not guaranteed to have properties or behaviors of subclass
- Invalid downcasting to assign a superclass object to a subclass reference will cause compile-time error
- Example of proper use:
  ```java
  Circle c = new ColoredCircle(p, 0, blue); // OK
  ```
- Example of improper use:
  ```java
  ColoredCircle c  = new Circle(p, 0); // error
  ```

## Run-Time Type
- Compile-time type: Declared type of variable
- Run-time type: Actual type of object
- Example:
  ```java
  Shape s = new Circle(p, 1.0); 
  // Compile-time type: Shape
  // Run-time type: Circle
  ```

## Compile-Time Type
- Java does not use the information from run-time type
- Java will only use compile-time type information for type checking
- Java compiler checks methods based on compile-time type, not run-time type.
- Example:
  ```java
  class T {
    public int foo() {
      return 0;
    }
  }
  class S1 extends T {
    public int bar() {
      return 1;
    }
  }
  class S2 extends T {
    public int baz() {
      return 2;
    }
  }
  ```
  ```java
  T x = new S1();
  x = new S2();  // re-assignment
  // Re-assignment is valid as S1 <: T and S2 <: T based on compile-time type 
  ```
  ```java
  T x = new S1();
  x.bar(); // error
  // Based on compile-time type, Type T has no method bar()
  // Even if run-time type to have the method bar(), it is still irrelevant during compile-time checking
  ```

## Nominal Subtyping
- Java subtyping relationship is known as nominal subtyping
- Subtyping relationship must be explicitly declared
- `extends` keyword to declare subtyping relationship
- Java prevents a cyclic subtyping
- Example:
  ```java
  class A extends B {
  }

  class B extends A {
  } // Cyclic inheritance error
  ```

## Best Practices
- Use inheritance sparingly
- Prefer composition over inheritance
- Ensure IS-A relationship exists
- Document inheritance relationships
- Keep inheritance hierarchies shallow
- Consider making classes final if not meant for inheritance
