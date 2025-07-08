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
        - Static method exists without instantiating the class 
        - `this` refers to a specific object instance, which static methods do not have 
  
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
      this.x = 1;  // Error: cannot use `this`
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
- Passed to `String[]` array of main method
- `args` parameter stores command line arguments
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
    - Utility functions that perform general operations and don't depend on instance state (data)
        - Example:
        ```java
        class MathUtils {
          public static int square(int x) {
            return x * x;
          }
        }
        ```
    - Accessing or managing static fields
        - Example:
        ```java
        class Circle {
          private final int id;
          private static int lastId = 0;

          public Circle() {
            this.id = Circle.lastId;
            Circle.lastId += 1;
          }

          // Access static field
          public static int getNumOfCircles() {
            return Circle.lastId;
          }
        }
        ```
    - Factory methods
- Keep static methods independent of instance state
- Consider making utility classes final
- Document command line arguments clearly

## Factory Methods
- Static methods that create objects
- Benefits:
  1. When object creation needs to be controlled 
  2. Better naming than constructors
  3. Can return cached instances
  4. Can return different subtypes 

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


> Notes:
- Static methods and inheritance
    - Static methods are not overridden, they are hidden
    - Call is resolved at compile time, based on the reference type
    - Example:
      ```java
      class A {
        static void sayHello() {
          System.out.println("Hello from A");
        }
      }

      class B extends A {
        static void sayHello() {
          System.out.println("Hello from B");
        }
      }

      A a = new B();
      a.sayHello(); // prints: Hello from A
      ```

- Static method vs Singleton pattern
    - Use Static Method:
        - When you have utility methods that do not require state.
        - When thread safety and shared mutable state are not concerns.
    - Use Singleton:
        - When you need a single, globally accessible instance with mutable state.
        - When managing resources that should be shared among multiple parts of the application.

- Thread safety in static methods
    - Static methods can become unsafe in a multithreaded context if:
        - Modify static mutable fields
        - Depend on shared resources
    - Use `synchronized` or other concurrency controls when necessary

- Use in testing and mocking
    - Static methods are harder to mock in unit tests.
    - Best to avoid static if testability is a priority.
    - Frameworks like PowerMockito can be used to mock static methods.