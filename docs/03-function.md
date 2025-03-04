# Functions Summary

## Computation Abstraction: Functions
- Functions group instructions and give them a name
- Allow composition at higher levels of abstraction
- Basic Java function syntax:
  ```java
  return_type function_name(param_type1 param1, param_type2 param2) {
    function body
  }
  ```
- Return type is mandatory (use `void` if no return value)
- Java doesn't support returning multiple values

## Benefits of Functions

### Compartmentalization
- Isolates computation and effects
- Limits interactions to parameters and return values
- Reduces number of variables to track
- Contains complexity within function body

### Implementation Hiding
- Hides how a task is performed
- Caller only needs to know what function does
- Reduces information needed between programmers
- Allows implementation changes without affecting callers

### Code Reuse
- Reduces repeated code through parameterization
- Makes code more succinct and readable
- Reduces places that need modification when code evolves
- Decreases chance of introducing bugs

## Abstraction Barrier
- Separates code that calls function from code that implements function
- Divides programmer roles:
    - Implementer: provides implementation
    - Client: uses the function
- Enforces separation of concerns
- Allows implementation changes without affecting client code
- Protects implementation details from client

## Pure Functions
- Functions that behave like mathematical functions
- Given same input, always produce same output
- Have no side effects (don't modify external state)
- Example:
  ```java
  int square(int i) {
    return i * i;
  }
  ```

## Non-Pure Functions
- May throw exceptions
- May modify external state
- May depend on external state
- May not return a value
- Example:
  ```java
  void addToQueue(Queue<Integer> queue, int i) {
    queue.enq(i);  // has side effects on queue
  }
  ```

## Variable Arguments (Varargs)
- Allows methods to accept variable number of arguments
- Uses ellipsis (`...`) in parameter declaration
- Must be the last parameter in method signature
- Internally treated as an array
- Example:
  ```java
  void printAll(String... messages) {
    for (String msg : messages) {
      System.out.println(msg);
    }
  }
  ```
- Can be called with:
  ```java
  printAll("Hello");                    // one argument
  printAll("Hello", "World");          // two arguments
  printAll("A", "B", "C", "D");        // multiple arguments
  printAll();                          // zero arguments
  ```
- Can also be called with an array:
  ```java
  String[] messages = {"A", "B", "C"};
  printAll(messages);                   // passing array directly
  ```
