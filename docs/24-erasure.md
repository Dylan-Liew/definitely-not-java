# Type Erasure Summary

## Type Erasure Concept
- Java's implementation of generics
- Removes type parameters at compile time
- Replaces with Object or bounds
- Maintains backward compatibility
- Example:
  ```java
  // Before erasure
  class Box<T> {
    private T item;
  }
  
  // After erasure
  class Box {
    private Object item;  // T replaced with Object
  }
  ```

## How Erasure Works
- Replaces type parameters with Object
- Replaces bounded types with first bound
- Adds type casts where necessary
- Example:
  ```java
  // Before erasure
  Box<String> box = new Box<>();
  String s = box.get();
  
  // After erasure
  Box box = new Box();
  String s = (String) box.get();
  ```

## Erasure with Bounds
- Bounded type replaced with bound
- Example:
  ```java
  // Before erasure
  class NumberBox<T extends Number> {
    private T number;
  }
  
  // After erasure
  class NumberBox {
    private Number number;  // T replaced with Number
  }
  ```

## Arrays and Generics
- Cannot create arrays of generic types
- Type information lost at runtime
- Can lead to heap pollution
- Example:
  ```java
  // Not allowed:
  T[] array = new T[10];
  
  // Common workaround:
  T[] array = (T[]) new Object[10];
  ```

## Reifiable Types
- Types with runtime information available
- Includes:
    - Primitive types
    - Non-generic types
    - Raw types
    - Unbounded wildcards
- Example:
  ```java
  // Reifiable
  String[] strings = new String[10];
  List<?> list = new ArrayList<>();
  
  // Not reifiable
  List<String>[] arrayOfLists;  // compile error
  ```

## Best Practices
- Be aware of type erasure limitations
- Use runtime type tokens when needed
- Avoid mixing arrays and generics
- Document type erasure implications
- Use collections over arrays with generics
- Consider reifiable type alternatives
