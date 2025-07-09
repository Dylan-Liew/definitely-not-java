# Heap and Stack Summary

## JVM Memory Regions
- Method area: Stores method code
- Metaspace: Stores class metadata
- Heap: Stores dynamically allocated objects
- Stack: Stores local variables and call frames

## Stack
- Contains variables (not instance/class fields)
- Organized in call frames
- LIFO (Last-In-First-Out) structure
- Call frames:
    - Created when method invoked
    - Removed when method completes
    - Contains local variables
    - Contains method parameters
    - Contains reference to `this` (for non-static methods)

## Heap
- Stores objects created with `new`
- Objects persist across method calls
- Can be shared between methods
- Contains:
    - Class name
    - Instance fields and values
    - Captured variables (Nested Class)
- No LIFO restriction

## Example Stack and Heap Interactions
```java
Point p;                  // Stack: p (uninitialised)

p = new Point(1, 2);      // Heap: Point object
                          // Stack: p (reference to Point)
                          // Creates call frame for Point constructor

```
=== "After Line 1"
    ![After Line 1](image/heap-and-stack-point-afterLine1.png)
=== "Allocate Memory"
    ![Allocate Memory](image/heap-and-stack-point-allocateMemory.png)
=== "Invoke Constructor"
    ![Invoke Constructor](image/heap-and-stack-point-invokeConstructor.png)
=== "End of Constructor"
    ![End of Constructor](image/heap-and-stack-point-endOfConstructor.png)
=== "Return from Constructor"
    ![Return from Constructor](image/heap-and-stack-point-returnFromConstructor.png)
- Symbol ∅ to indicate that the variable is not yet initialized
- For presentation, memory address (e.g., 9048ab50) will be omitted 
- Each constructor call creates a new frame
- Frame contains:
    - `this` reference
    - Constructor parameters
    - Local variables 

## Constructor Example
```java
Point p1 = new Point(0, 0);  // Creates call frame for Point constructor
Point p2 = new Point(1, 1);  // Creates new call frame
```

## Method Call Example
```java
class Point {
  private double x;
  private double y;

  public Point(double x, double y) {
    this.x = x;
    this.y = y;
  }

  public void move(double x, double y) {
    this.x = x;
    this.y = y;
  }
}
```

```java
Point p1 = new Point(0, 0);
Point p2 = new Point(1, 1);
double x = 5;
double y = 5;
p1.move(x, y);
```
=== "After Lines 1-2"
    ![After Line 1-2](image/method-call-example-afterLine1-2.png)
=== "After Lines 3-4"
    ![Allocate Memory](image/method-call-example-afterLine3-4.png)
=== "Method Invocation at Line 5"
    ![Invoke Constructor](image/method-call-example-methodInvocationatLine5.png)
=== "After Line 5"
    ![End of Constructor](image/method-call-example-afterLine5.png)

- Method call creates new frame
- Frame destroyed after method returns
- Parameters copied to new frame

## Call Stack Behavior
- Methods can be nested
- Each nested call adds new frame
- Frames removed in reverse order
- Example:
  ```java
  a() {
    b();      // b's frame stacked on a's
    return;   // b's frame removed, back to a's
  }
  ```

## Best Practices
- Understand object lifetime
- Be aware of object sharing
- Consider stack vs heap allocation
- Clean up references when no longer needed
- Be mindful of memory usage patterns
