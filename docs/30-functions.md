# Functions Summary

## Pure Functions
- No side effects
- Same input always gives same output
- Deterministic behavior
- Example:
  ```java
  int square(int x) {
    return x * x;  // pure function
  }
  ```

## First-Class Functions
- Functions as values
- Can be passed as arguments
- Can be returned from methods
- Can be stored in variables
- Example:
  ```java
  interface Transformer<T,R> {
    R transform(T t);
  }
  
  Transformer<Integer,Integer> square = x -> x * x;
  ```

## Lambda Expressions
- Anonymous function syntax
- Concise method definitions
- Used with functional interfaces
- Example:
  ```java
  // Lambda syntax variations
  x -> x + 1                    // single parameter
  (x, y) -> x + y              // multiple parameters
  (String s) -> s.length()     // with type
  x -> { return x * x; }       // with block
  ```

## Method References
- Shorthand for lambdas
- References existing methods
- Four types:
    1. Static methods
    2. Instance methods
    3. Constructor references
    4. Arbitrary object methods
- Example:
  ```java
  String::length              // instance method
  System.out::println        // instance method
  Integer::parseInt         // static method
  ArrayList::new           // constructor
  ```

## Currying
- Converting n-ary function to sequence of unary functions
- Enables partial application
- Example:
  ```java
  // Instead of:
  int add(int x, int y) {
    return x + y;
  }
  
  // Curried version:
  Function<Integer, Function<Integer, Integer>> 
    curriedAdd = x -> y -> x + y;
  ```

## Closures
- Functions that capture their environment
- Access to non-local variables
- Example:
  ```java
  int multiplier = 10;
  Transformer<Integer,Integer> times = x -> x * multiplier;
  ```

## Best Practices
- Prefer pure functions
- Use meaningful names
- Keep functions small and focused
- Document behavior
- Consider composability
- Handle edge cases
- Test thoroughly
