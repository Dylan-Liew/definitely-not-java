# Liskov Substitution Principle Summary

## LSP Definition
- Subtype must be completely substitutable for its supertype
- Subtype must preserve behavior expected of supertype
- **Formal Definition**: Let φ(x) be a property provable about objects x of type T. Then φ(y) should be true for objects y of type S where S <: T
- A subclass should pass all test cases of its superclass

## Preventing Inheritance
- Use `final` keyword to prevent inheritance
- Example:
```java
final class String {  // Cannot be inherited
  // implementation
}
```

## Preventing Method Overriding
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

## Best Practices
- Design inheritance hierarchies carefully
- Document expected behavior and constraints
- Use `final` when inheritance not intended
- Test subclasses against superclass contracts
- Consider composition over inheritance
- Make classes immutable when possible
- Write clear specifications for methods
