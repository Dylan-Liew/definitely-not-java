# Static Field Summary

## Class Fields (Static Fields)
- Fields associated with class rather than instances
- Declared using `static` keyword
- Shared across all instances of the class
- Can be accessed without creating class instance
- Example:
  ```java
<<<<<<< HEAD
  // Universal field: PI
=======
>>>>>>> 894be436c0b17707585c67c478dfebd5ce9f6884
  class Math {
    public static final double PI = 3.141592653589793;
  }
  ```

## Common Modifiers for Class Fields
- `static`: Makes field belong to class
- `final`: Makes field value unchangeable
- `public`: Makes field accessible outside class
<<<<<<< HEAD
- Common combination: `public static final` for defining globally accessible constants.

## Accessing Class Fields
- Access through class name: `Math.PI`
- Example:
  ```java
  public double getArea() {
  return java.lang.Math.PI * this.r * this.r;
  }
  ```
=======
- Common combination: `public static final` for constants

## Accessing Class Fields
- Access through class name: `Math.PI`
>>>>>>> 894be436c0b17707585c67c478dfebd5ce9f6884
- Can use import statement to simplify access
- Example:
  ```java
  import java.lang.Math;
<<<<<<< HEAD
  
  // Now can use Math.PI directly
  public double Circumference() {
    return Math.PI * this.r * 2;
  }
  ```

## Instance Fields vs Class Fields
- Instance fields (Non-static field):
    - Belong to specific object instances
    - Each object has its own separate copy of the field
    - Accessed through object reference
  
- Class fields (static field):
    - Belong to class itself
    - Single copy shared by all instances
    - Accessed through class name
    - Loaded into memory when class is loaded by JVM, even if no objects are created
=======
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
>>>>>>> 894be436c0b17707585c67c478dfebd5ce9f6884

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
<<<<<<< HEAD

> Notes: 
- Lifecycle and Memory behavior:
    - Static fields are initialised exactly once when the class is first loaded by the JVM.
    - static fields may lead to memory leaks if it stores large objects like Lists or Maps in them. 
      Additionally, if forget to clear the large objects, they will never get garbage collected.
    - Static blocks for complex static initalisation
        - Example:
        ```java
        static {
          CONFIG = loadConfig("app.properties");
        }
        ```
- Sharing and Access behavior:
    - Instance-specific data like `name`, `balance` or `id` should NOT be static
    - Good practice in accessing static fields using class name, not object reference
    - All fields in interfaces are implicitly public, static and final.

- Immutability and Thread safety
    - Mutable static fields are shared by all threads, needs synchronization if shared across threads
    - Final instance fields are immutable.

- Design Patterns
    - Use static fields for configuration or constants like `MAX_USERS`, not temporary or user-specific values.
    - Static fields can be used for shared logic or metadata across tightly controlled subclasses.
        - Example:
          ```java
          // A sealed class with only Circle and Square are allowed to extend Shape
          public sealed class Shape permits Circle, Square {
            public static final String TYPE = "2D";
          } 
          ```
=======
>>>>>>> 894be436c0b17707585c67c478dfebd5ce9f6884
