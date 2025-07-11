# Variance Summary

## Variance Concepts
- Describes subtyping relationships between complex types
- Three types of variance:
    1. Covariant: If S <: T then C(S) <: C(T)
    2. Contravariant: If S <: T then C(T) <: C(S)
    3. Invariant: No subtyping relationship

## Java Array Covariance
- Arrays are covariant in Java
- Can lead to runtime errors
- Example:
  ```java
  Integer[] intArray = new Integer[2];
  Object[] objArray = intArray;        // OK due to covariance
  objArray[0] = "Hello";              // Runtime error!
  ```

## Problems with Array Covariance
- Type safety compromised
- Runtime errors possible
- Example of unsafe code:
  ```java
  Shape[] shapes = new Circle[2];    // allowed
  shapes[0] = new Square(1.0);       // runtime error
  ```

## Variance in Generics
- Generic types are invariant by default
- Example:
  ```java
  List<Circle> circles = new ArrayList<>();
  List<Shape> shapes = circles;  // compile error
  ```

## Safe Use of Variance
- Use generics instead of arrays when possible
- Be cautious with array covariance
- Consider using wildcards for flexibility
- Example:
  ```java
  // Safe generic usage
  List<Circle> circles = new ArrayList<>();
  List<? extends Shape> shapes = circles;  // OK with wildcard
  ```

## Best Practices
- Prefer generics over arrays
- Be aware of array covariance pitfalls
- Use wildcards appropriately
- Design for type safety
- Test edge cases with different types
- Document variance relationships
