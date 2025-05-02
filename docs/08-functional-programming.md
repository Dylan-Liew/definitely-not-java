# Functional Programming

## Functions as First-Class Citizens

### Pure Functions
- No side effects 
  - No printing to screen
  - No writing to files
  - No throwing exceptions
  - No changing other variables
- Same input always gives same output
- Example:
  ```java
  int square(int x) {
    return x * x;  // pure function
  }
  ```

### First-Class Functions
- Functions as values
- Can be passed as arguments
- Can be returned from methods
- Can be stored in variables
- Example:
  ```java
  @FunctionalInterface
  interface Transformer<T,R> {
    R transform(T t);
  }
  
  Transformer<Integer,Integer> square = x -> x * x;
  ```

### Lambda Expressions
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

### Method References
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

## Nested Classes

### Types of Nested Classes
1. Inner Classes
   - Has access to all outer class members
   - Requires instance of outer class

2. Static Nested Classes
   - Declared with static modifier
   - Cannot access instance members of outer class

3. Local Classes
   - Defined inside methods
   - Can access local variables (must be final/effectively final)

4. Anonymous Classes
   - Class definition and instantiation combined
   - Example:
     ```java
     Runnable r = new Runnable() {
       @Override
       public void run() {
         System.out.println("Hello");
       }
     };
     ```

## Functional Data Types

### Box<T> and Maybe<T>
- Generic containers for values
- Enable functional operations
- Maybe handles optional values safely
- Example:
  ```java
  // Map example
  Maybe<String> name = Maybe.some("hello");
  Maybe<Integer> length = name.map(s -> s.length());
  
  // FlatMap example
  Maybe<Maybe<String>> nested = Maybe.some(Maybe.some("hello"));
  Maybe<String> flattened = nested.flatMap(x -> x);
  ```

### Lazy Evaluation
- Delays computation until needed
- Avoids unnecessary calculations
- Uses memoization to cache results
- Example:
  ```java
  class Lazy<T> {
    private T value;
    private boolean evaluated;
    private Producer<T> producer;
    
    public T get() {
      if (!evaluated) {
        value = producer.produce();
        evaluated = true;
      }
      return value;
    }
  }
  ```

### InfiniteList
- Represents potentially infinite sequences
- Lazily evaluated
- Uses head/tail structure
- Example:
  ```java
  InfiniteList<Integer> numbers = InfiniteList
    .iterate(0, x -> x + 1)     // 0,1,2,3,...
    .filter(x -> x % 2 == 0)    // 0,2,4,6,...
    .map(x -> x * x)            // 0,4,16,36,...
    .limit(5);                  // first 5 elements
  ```

### Monads
- Container type with specific behavior rules
- Supports sequential operations
- Maintains computational context
- Laws:
  1. Left Identity
  2. Right Identity
  3. Associativity
