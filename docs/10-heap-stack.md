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
    - Captured variables
- No LIFO restriction

## Example Stack and Heap Interactions
```java
Point p;                    // Stack: p (uninitialized)
p = new Point(1, 2);       // Heap: Point object
                          // Stack: p (reference to Point)

Circle c = new Circle(p, 3); // Heap: Circle object
                           // Stack: c (reference to Circle)
```

## Constructor Example
```java
Point p1 = new Point(0, 0);  // Creates call frame for Point constructor
Point p2 = new Point(1, 1);  // Creates new call frame
```
- Each constructor call creates new frame
- Frame contains:
    - `this` reference
    - Constructor parameters
    - Local variables

## Method Call Example
```java
void foo(Point p) {
  int x = p.getX();  // Creates call frame for getX
}
```
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
