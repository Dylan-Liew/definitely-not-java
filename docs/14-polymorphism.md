# Polymorphism Summary

## Polymorphism Concept
- Ability of objects to take multiple forms
- Method behavior depends on object's runtime type
- Enables code reuse and flexibility
- Example:
  ```java
  Shape s = new Circle(p, 1.0);  // Circle behaves as a Shape
  s.getArea();  // calls Circle's getArea method
  ```

## Dynamic Binding
- Method calls resolved at runtime
- Based on actual object type, not variable type
- Also called late binding
- Example:
  ```java
  void say(Object obj) {
    System.out.println(obj.toString());  // calls appropriate toString
  }
  ```

## Type Casting
- Converting between supertype and subtype
- Widening conversion (subtype to supertype):
    - Automatic
    - Always safe
  ```java
  Circle c = new Circle(p, 1.0);
  Shape s = c;  // widening, no cast needed
  ```
- Narrowing conversion (supertype to subtype):
    - Requires explicit cast
    - May cause runtime errors
  ```java
  Shape s = new Circle(p, 1.0);
  Circle c = (Circle) s;  // narrowing, needs cast
  ```

## instanceof Operator
- Checks object's runtime type
- Used before casting to prevent errors
- Example:
  ```java
  if (obj instanceof Circle) {
    Circle c = (Circle) obj;  // safe cast
    // use c
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
