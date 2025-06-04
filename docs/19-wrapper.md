# Wrapper Classes Summary

## Wrapper Class Concept
- Classes that encapsulate primitive types
- Convert primitives to objects
- Provide utility methods
- Enable use of primitives in generic code
- Example:
  ```java
  Integer i = new Integer(42);  // wraps int
  Double d = new Double(3.14);  // wraps double
  ```

## Java Wrapper Classes
| Primitive | Wrapper |
|-----------|---------|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

## Auto-boxing and Unboxing
- Auto-boxing: Automatic primitive to wrapper conversion
- Unboxing: Automatic wrapper to primitive conversion
- Example:
  ```java
  Integer i = 42;    // auto-boxing
  int n = i;         // unboxing
  ```

## Performance Considerations
- Wrapper objects have overhead
- Creating new wrapper objects is expensive
- Example of inefficient code:
  ```java
  Double sum = 0.0;
  for (int i = 0; i < 1000000; i++) {
    sum += i;  // creates new Double object each time
  }
  ```

## Utility Methods
- Parsing methods
- Value conversions
- Comparisons
- Example:
  ```java
  Integer.parseInt("123");     // String to int
  Integer.toString(123);       // int to String
  Integer.valueOf("123");      // String to Integer
  Integer.compare(1, 2);       // compare two ints
  ```

## Best Practices
- Use primitives for performance-critical code
- Use wrappers when objects are required
- Be aware of auto-boxing overhead
- Use static utility methods when possible
- Consider memory usage in collections
- Avoid null wrapper objects
