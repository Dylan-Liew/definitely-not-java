# Method Overriding Summary

## Object Class
- Every class implicitly inherits from `Object`
- `Object` provides common methods:
    - `equals(Object obj)`: Check equality
    - `toString()`: String representation
    - `hashCode()`: Hash value
    - Others like `clone()`, `finalize()`

## Method Overriding
- Subclass provides new implementation of parent's method
- Must have same method descriptor as parent
- Enables polymorphic behavior
- Example:
  ```java
  class Circle {
    @Override
    public String toString() {
      return "Circle with radius " + this.r;
    }
  }
  ```

## Rules for Overriding
- Method must have:
    - Same name
    - Same parameters (number, type, order)
    - Same return type (or covariant)
    - Same or less restrictive access
- Cannot override:
    - `final` methods
    - `static` methods
    - `private` methods

## @Override Annotation
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

## Using super with Overridden Methods
- Access parent's version using `super`
- Useful when extending behavior
- Example:
  ```java
  @Override
  public String toString() {
    return super.toString() + " (custom info)";
  }
  ```

## Common Methods to Override
- `toString()`: String representation
- `equals(Object)`: Object equality
- `hashCode()`: Hash code for hash-based collections
- Example:
  ```java
  @Override
  public boolean equals(Object obj) {
    if (obj instanceof Circle) {
      Circle other = (Circle) obj;
      return this.radius == other.radius;
    }
    return false;
  }
  ```

## Best Practices
- Always use @Override annotation
- Override toString() for debugging
- Override equals() and hashCode() together
- Keep overridden methods consistent with parent's contract
- Document overridden behavior
