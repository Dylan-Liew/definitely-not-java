# Method Overloading Summary

## Method Overloading Concept
- Multiple methods with same name but different parameters 
- Based on [method signature](12-overriding.md#method-signature) differences
- Example:
  ```java
  class Calculator {
    public int add(int x, int y) { return x + y; }
    public int add(int x, int y, int z) { return x + y + z; }
    public double add(double x, double y) { return x + y; }
  }
  ```

## Valid vs Invalid Overloading
- Valid overloading:
  ```java
  void process(int x, double y) { }
  void process(double x, int y) { }    // Different parameter order
  void process (double x, double y) { } // Different parameter types
  void process(int x, int y, int z) { } // Different number of parameters
  ```
- Invalid overloading:
  ```java
  int process(int x, int y) { }
  double process(int x, int y) { }     // Only return type differs
  void process(int a, int b) { }       // Only parameter names differ
  ```

## Constructor Overloading
- Constructors can also be overloaded
- Multiple constructors with different parameters provide flexibility for object initialization
- Example:
  ```java
  class Circle {
    private Point center;
    private double radius; 

    public Circle(Point center, double radius) { 
      this.center = center;
      this.radius = radius;
    }

    public Circle() {  // Default constructor
      this(new Point(0, 0), 1.0);  // Calls other constructor
    }

    public Circle(double radius) {  // Single parameter constructor
      this(new Point(0, 0), radius);
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
