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
- Example:
  ```java
  class ColoredCircle extends Circle {
    public ColoredCircle(Point center, double radius, Color color) {
      super(center, radius);  // call parent constructor
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

## Run-Time Type
- Compile-time type: Declared type of variable
- Run-time type: Actual type of object
- Example:
  ```java
  Shape s = new Circle(p, 1.0);
  // Compile-time type: Shape
  // Run-time type: Circle
  ```

## Best Practices
- Use inheritance sparingly
- Prefer composition over inheritance
- Ensure IS-A relationship exists
- Document inheritance relationships
- Keep inheritance hierarchies shallow
- Consider making classes final if not meant for inheritance
