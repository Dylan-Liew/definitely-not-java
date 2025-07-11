# Static Field Summary

## Class Fields (Static Fields)
- Fields associated with class rather than instances
- Declared using `static` keyword
- Shared across all instances of the class
- Can be accessed without creating class instance
- Example:
  ```java
  // Universal field: PI
  class Math {
    public static final double PI = 3.141592653589793;
  }
  ```

## Common Modifiers for Class Fields
- `static`: Makes field belong to class
- `final`: Makes field value unchangeable
- `public`: Makes field accessible outside class
- Common combination: `public static final` for defining globally accessible constants.

## Accessing Class Fields
- Access through class name: `Math.PI`
- Example:
  ```java
  public double getArea() {
    return java.lang.Math.PI * this.r * this.r;
  }
  ```
- Can use import statement to simplify access
- Example:
  ```java
  import java.lang.Math;
  
  // Now can use Math.PI directly
  public double Circumference() {
    return Math.PI * this.r * 2;
  }
  ```

## Instance Fields vs Class Fields
- Instance fields (non-static field):
    - Belong to specific object instances
    - Each object has its own separate copy of the field
    - Accessed through object reference
  
- Class fields (static field):
    - Belong to class itself
    - Single copy shared by all instances
    - Accessed through class name
    - Loaded into memory when class is loaded by JVM, even if no objects are created

## Best Practices
- Use class fields for:
    - Constants
    - Values shared across all instances
    - Configuration parameters
    - Pre-computed values
- Make class fields final when possible
- Use meaningful names for constants
- Consider using existing constants (e.g., Math.PI)
