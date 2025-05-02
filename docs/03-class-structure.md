# Class Structure

## Static Fields (Class Fields)

### Class Field Concept
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

### Common Modifiers for Class Fields
- `static`: Makes field belong to class
- `final`: Makes field value unchangeable
- `public`: Makes field accessible outside class
- Common combination: `public static final` for constants

### Instance vs. Class Fields
- Instance fields:
    - Belong to specific object instances
    - Each instance has its own copy
    - Accessed through object reference
  
- Class fields:
    - Belong to class itself
    - Single copy shared by all instances
    - Accessed through class name
    - Exist even if no instances created

## Static Methods (Class Methods)

### Class Method Concept
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

### Static vs Non-Static Methods
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

### The main Method
- Special static method as program entry point
- Required signature:
  ```java
  public static void main(String[] args)
  ```

### Factory Methods
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

## Memory Management Basics

### JVM Memory Regions
- Method area: Stores method code
- Heap: Stores dynamically allocated objects
- Stack: Stores local variables and call frames

### Object Lifecycle
- Objects created with `new` on the heap
- References stored on stack or as fields in other objects
- Objects persist across method calls
- Garbage collector reclaims unreferenced objects
- Example:
  ```java
  void method() {
    Circle c = new Circle(0, 0, 5);  // c on stack, Circle on heap
    doSomething(c);                  // reference passed
  }  // c goes out of scope, Circle may be garbage collected
  ```
