# Polymorphism Summary

## Polymorphism Concept
- Ability of object reference variables to take multiple forms
- Method behavior depends on object's runtime type
- Enables code reuse and flexibility
- Example:
  ```java
  Animal i; // i is Animal

  i = new Dog(); // i takes Dog form
  i.speak(); // prints: Dog barks

  i = new Cat(); // i can also take Cat form
  i.speak(); // prints: Cat meows
  ```

## The `equals` Method
- Object::equals(Object) compares if two object references refer to the same object. 
- The reference is the memory address of objects
- Properties:
    - Reflexive: `x.equals(x)` must return `true`
    - Symmetric: `x.equals(x)` is `true` and `y.equals` must be `true`
    - Transitive: `x.equals(y)` and `y.equals(z)` are true, then `x.equals(z)` must be `true`
    - Non-null: `x.equals(null)` must return `false`
    - Usage: `obj.equals(arg)` and `obj` must not be `null`
- `equals` method example:
  ```java
  Circle c0 = new Circle(new Point(0, 0), 10);
  Circle c1 = new Circle(new Point(0, 0), 10);
  Circle c2 = c1;
  // c2.equals(c1) returns true (same object reference)
  // c0.equals(c1) returns false (different objects in memory)

  // Even though c0 and c1 are semantically identical,
  // they are different objects with different memory addresses
  ```

## Overriding equals for Semantic Equality
- To compare objects based on their content rather than memory address, override the `equals` method:
  ```java
  @Override
  public boolean equals(Object obj) {
    if (this == obj) return true;
    if (obj instanceof Circle) {
      Circle circle = (Circle) obj;
      return (circle.c.equals(this.c) && circle.r == this.r);
    }
    return false;
  }
  // Must take Object parameter
  // Use instanceof or getClass() to check runtime type before casting
  // Explicit downcast needed to access subclass-specific fields
  // A class can access private members of any object of the same class
  // Override must have the same method descriptor as the parent class
  ```

## Dynamic Binding
- Method calls resolved at runtime
- Based on actual object type, not variable type
- Also called late binding
- Example:
  ```java
  boolean contains(Object[] array, Object obj) {
    for (Object curr : array) {
      if (curr.equals(obj)) {
        return true;
      }
    }
    return false;
  }

  // At compile time, curr is known as Object type
  // At runtime, based on curr's actual type:
  // - If curr is Circle, invoke Circle.equals(Object)
  // - If curr is Point, invoke Point.equals(Object)  
  // - If curr is String, invoke String.equals(Object)
  ```

## Type Casting 
- Converting between supertype and subtype
- Widening conversion (subtype to supertype):
    - Automatic
    - Always safe
  ```java
  Circle c = new Circle(new Point(0, 0), 1.0);
  Shape s = c;  // Widening conversion - no cast needed
  Object obj = c;  // Also widening - completely safe
  ```
- Narrowing conversion (supertype to subtype):
    - Requires explicit cast
    - May cause runtime errors
  ```java
  Shape s = new Circle(new Point(0, 0), 1.0);
  Circle c = (Circle) s;  // Narrowing conversion - explicit cast required

  // Dangerous without checking:
  Shape s2 = new Rectangle(1, 2);
  Circle c2 = (Circle) s2;  // ClassCastException at runtime!
  ```

## instanceof Operator
- Checks object's runtime type
- Used before casting to prevent errors
- Example:
  ```java
  public void processShape(Shape shape) {
      if (shape instanceof Circle) {
          Circle c = (Circle) shape;  // Safe cast
          System.out.println("Circle with radius: " + c.getRadius());
      } else if (shape instanceof Rectangle) {
          Rectangle r = (Rectangle) shape;  // Safe cast
          System.out.println("Rectangle: " + r.getWidth() + "x" + r.getHeight());
      }
  }
  ```

## Benefits of Polymorphism
- Write more general code
- Code works with future subclasses
- Reduces code duplication
- Example:
  ```java
  // Works with any Shape subclass
  double totalArea(Shape[] shapes) {
    double total = 0;
    for (Shape s : shapes) {
      total += s.getArea();  // polymorphic call
    }
    return total;
  }
  ```

## Best Practices
- Design for polymorphism when inheritance is used
- Use most general type in declarations
- Cast only when necessary
- Always check with instanceof before casting
- Document expected behavior of polymorphic methods
