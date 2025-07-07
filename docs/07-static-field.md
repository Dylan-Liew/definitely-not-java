# Static Field Summary

## Class Fields (Static Fields)
- Fields associated with class rather than instances
- Declared using `static` keyword
- Shared across all instances of the class
- Can be accessed without creating class instance
- Example:
  ```java
  class Math {
    public static final double PI = 3.141592653589793;
  }
  ```

## Common Modifiers for Class Fields
- `static`: Makes field belong to class
- `final`: Makes field value unchangeable
- `public`: Makes field accessible outside class
- Common combination: `public static final` for constants

## Accessing Class Fields
- Access through class name: `Math.PI`
- Can use import statement to simplify access
- Example:
  ```java
  import java.lang.Math;
  // Now can use Math.PI directly
  ```

## Instance Fields vs Class Fields
- Instance fields:
    - Belong to specific object instances
    - Each instance has its own copy
    - Accessed through object reference
  
- Class fields:
    - Belong to class itself
    - Single copy shared by all instances
    - Accessed through class name
    - Exist even if no instances created

## Example Usage
```java
class Circle {
  private Point c;
  private double r;
  public static final double PI = Math.PI;  // class field

  public double getArea() {
    return PI * this.r * this.r;  // using class field
  }
}
```

## Best Practices
- Use class fields for:
    - Constants
    - Values shared across all instances
    - Configuration parameters
    - Pre-computed values
- Make class fields final when possible
- Use meaningful names for constants
- Consider using existing constants (e.g., Math.PI)
