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
  // c2.equals(c1) returns true
  // c0.equals(c1) returns false

  // Even though c0 and c1 are semantically the same, 
  // but they are still 2 different objects with different memory addresses
  ```
- Override the `equals` method to compare objects semantically
- Overriding example:
  ```java
  @Override
  public boolean equals(Object obj) {
    if (obj instanceof Circle) {
      Circle circle = (Circle) obj;
      return (circle.c.equals(this.c) && circle.r == this.r);
    }
    return false;
  }
  // Takes in Object parameter, check runtime type of the parameter is an instance of Circle
  // Explicitly downcast is needed to avoid complier error as the complie type of the parameter is Object
  
  // A class can access the private members of any object of the same class,
  // so that fields c and r are accessible even they are not belong to current Object

  // Override must have same method descriptor as parent
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
   // At compile time, the type is known as Object 

  // Based on the runtime type of curr, the customised version of equals can be called to compare against obj.

  // If runtime type of curr is Circle, invoke Circle::equals(Object)
  // If runtime type of curr is Point, invoke Point::equals(Object)
  boolean contains(Object[] array, Object obj) {
    for (Object curr : array) {
      if (curr.equals(obj)) {
        return true;
      }
    }
    return false;
  }
   // At compile time, the type is known as Object 

  // Based on the runtime type of curr, the customised version of equals can be called to compare against obj.

  // If runtime type of curr is Circle, invoke Circle::equals(Object)
  // If runtime type of curr is Point, invoke Point::equals(Object)
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
