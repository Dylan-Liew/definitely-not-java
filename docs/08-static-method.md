# Static Method Summary

## Class Methods (Static Methods)
- Methods associated with class rather than instances
- Declared using `static` keyword
- Can be called without creating class instance
- Cannot access instance fields/methods directly
- Cannot use `this` keyword
- Example:
  ```java
  class Math {
    public static double sqrt(double x) {
      // compute square root
    }
  }
  ```

## Static vs Non-Static Methods
- Static methods:
    - Belong to class
    - Can only access static members
    - Called through class name
    - No access to `this`
  
- Non-static methods:
    - Belong to instances
    - Can access all members
    - Called through instance
    - Has access to `this`

## Non-Static from Static Context
- Static methods cannot access:
    - Instance fields
    - Instance methods
    - `this` reference
- Example of invalid code:
  ```java
  class A {
    private int x;
    public static void foo() {
      this.x = 1;  // Error: cannot use this
      x = 1;       // Error: cannot access instance field
    }
  }
  ```

## The main Method
- Special static method as program entry point
- Required signature:
  ```java
  public static void main(String[] args)
  ```
- Characteristics:
    - Must be `public`
    - Must be `static`
    - Must return `void`
    - Must take String array parameter
    - Name must be `main`

## Command Line Arguments
- Passed to main method in String array
- Available through `args` parameter
- Example:
  ```java
  public static void main(String[] args) {
    // args[0] is first argument
    // args[1] is second argument
    // etc.
  }
  ```

## Best Practices
- Use static methods for:
    - Utility functions
    - Operations not requiring instance state
    - Factory methods
- Keep static methods independent of instance state
- Consider making utility classes final
- Document command line arguments clearly

## Factory Methods
- Static methods that create objects
- Benefits:
  1. Better naming than constructors
  2. Can return cached instances
  3. Can return different subtypes
  4. Control object creation

- Example:
  ```java
  public class Color {
    private final int red;
    private final int green;
    private final int blue;
    
    private Color(int r, int g, int b) {
      red = r;
      green = g;
      blue = b;
    }
    
    public static Color of(int r, int g, int b) {
      // Validation and caching logic here
      return new Color(r, g, b);
    }
    
  }
  ```