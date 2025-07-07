# Type Casting Summary

## Run-Time Class Mismatch
- Occurs when actual type doesn't match expected type
- Can lead to runtime errors
- Example:
  ```java
  GetAreable[] shapes = new GetAreable[] {
    new Circle(p, 2),
    new Square(p, 5)
  };
  Circle c = (Circle) shapes[1];  // Runtime error: Square cannot be cast to Circle
  ```

## Type Casting Basics
- Converting between compatible types
- Must be explicitly done for narrowing conversions
- Syntax: `(Type) expression`
- Example:
  ```java
  Shape s = new Circle(p, 1.0);
  Circle c = (Circle) s;  // explicit cast needed
  ```

## Safe Casting Practices
- Always check type before casting
- Use instanceof operator
- Example:
  ```java
  if (shape instanceof Circle) {
    Circle c = (Circle) shape;  // safe cast
    // use c
  }
  ```

## Common Casting Scenarios
1. Upcasting (Widening):
   ```java
   Circle c = new Circle(p, 1.0);
   Shape s = c;  // no cast needed
   ```

2. Downcasting (Narrowing):
   ```java
   Shape s = getShape();
   Circle c = (Circle) s;  // cast needed
   ```

## Casting with Generics
- Cannot create generic array
- Type erasure affects casting
- Example:
  ```java
  // Not allowed:
  T[] array = new T[10];  // compile error
  
  // Correct way:
  T[] array = (T[]) new Object[10];
  ```

## Best Practices
- Minimize use of casting
- Always validate types before casting
- Use generics when possible
- Document casting requirements
- Handle potential ClassCastException
- Design to avoid need for casting
