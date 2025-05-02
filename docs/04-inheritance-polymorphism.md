# Inheritance and Polymorphism

## Inheritance

### Inheritance Concept
- Mechanism to extend existing code
- Models "IS-A" relationship between classes
- Uses `extends` keyword in Java
- Example:
  ```java
  class ColoredCircle extends Circle {
    private Color color;
  }
  ```

### Key Characteristics
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

### When to Use Inheritance
- Use when subclass IS-A superclass
- Subclass should be substitutable for superclass
- Example of proper use:
  ```java
  // Square IS-A Shape
  class Square extends Shape { }
  ```

## Method Overriding

### Object Class
- Every class implicitly inherits from `Object`
- `Object` provides common methods:
    - `equals(Object obj)`: Check equality
    - `toString()`: String representation
    - `hashCode()`: Hash value

### Method Overriding Rules
- Method must have:
    - Same name
    - Same parameters (number, type, order)
    - Same return type (or covariant)
    - Same or less restrictive access
- Cannot override:
    - `final` methods
    - `static` methods
    - `private` methods

### @Override Annotation
- Indicates method is meant to override
- Helps catch errors at compile time
- Best practice to always use it
- Example:
  ```java
  @Override  // Compiler checks if parent has this method
  public boolean equals(Object obj) {
    // implementation
  }
  ```

## Method Overloading

### Method Overloading Concept
- Multiple methods with same name but different parameters
- Differs from overriding (which uses same parameters)
- Based on method signature differences
- Example:
  ```java
  class Calculator {
    public int add(int x, int y) { return x + y; }
    public int add(int x, int y, int z) { return x + y + z; }
    public double add(double x, double y) { return x + y; }
  }
  ```

### Method Signature Components
- Method name
- Parameter types
- Parameter order
- Number of parameters
- Does NOT include:
    - Return type
    - Parameter names
    - Access modifiers

## Polymorphism

### Polymorphism Concept
- Ability of objects to take multiple forms
- Method behavior depends on object's runtime type
- Enables code reuse and flexibility
- Example:
  ```java
  Shape s = new Circle(p, 1.0);  // Circle behaves as a Shape
  s.getArea();  // calls Circle's getArea method
  ```

### Dynamic Binding
- Method calls resolved at runtime
- Based on actual object type, not variable type
- Also called late binding
- Example:
  ```java
  void say(Object obj) {
    System.out.println(obj.toString());  // calls appropriate toString
  }
  ```

### Type Casting
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

## Liskov Substitution Principle

### LSP Definition
- Subtype must be completely substitutable for its supertype
- Subtype must preserve behavior expected of supertype
- A subclass should pass all test cases of its superclass

### Preventing Inheritance
- Use `final` keyword to prevent inheritance
- Example:
```java
final class String {  // Cannot be inherited
  // implementation
}
```

### Preventing Method Overriding
- Use `final` keyword on methods
- Prevents subclasses from changing behavior
- Example:
```java
class Circle {
  final double getArea() {  // Cannot be overridden
    return Math.PI * r * r;
  }
}
```
