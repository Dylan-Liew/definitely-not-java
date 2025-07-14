# Method Overloading Summary

## Method Overloading Concept
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

## Method Signature Components
- Method name
- Number of parameters
- Types of parameters
- Order of parameters
- Class name (Optional)
- Does NOT include:
    - Return type
    - Parameter names
    - Access modifiers

## Valid vs Invalid Overloading
- Valid overloading:
  ```java
  void process(int x, double y) { }
  void process(double x, int y) { }    // Different parameter order
  void process(int x, int y, int z) { } // Different number of parameters
  ```
- Invalid overloading:
  ```java
  int process(int x, int y) { }
  double process(int x, int y) { }     // Only return type differs
  void process(int a, int b) { }       // Only parameter names differ
  ```

## Constructor Overloading
- Multiple constructors with different parameters
- Common for providing different initialization options
- Example:
  ```java
  class Circle {
    public Circle(Point center, double radius) { }
    public Circle() {  // Default constructor
      this(new Point(0, 0), 1.0);  // Calls other constructor
    }
  }
  ```

## Static Method Overloading
- Static methods can be overloaded
- Same rules as instance methods
- Example:
  ```java
  class MathUtils {
    public static int max(int x, int y) { }
    public static double max(double x, double y) { }
    public static int max(int x, int y, int z) { }
  }
  ```

## Best Practices
- Use meaningful parameter variations
- Keep overloaded methods consistent
- Don't overload with similar parameter types
- Consider using different method names if behavior differs significantly
- Document differences between overloaded methods
