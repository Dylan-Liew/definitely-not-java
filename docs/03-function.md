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
- If returning multiple values is needed, use a data type that can store multiple values

## Benefits of Functions

### Compartmentalization
- Isolates computation and effects
- Limits interactions to parameters and return values
- Reduces number of variables to track
- Contains complexity within function body
- Example
  ```java
  int factorial(int n) {
    if (n == 0) {
      return 1;
    } else {
      return n * factorial(n - 1);
    }
  }
  
  // Approximation of e^n using Taylor series
  // e^n ≈ 1^0/0! + n^1/1! + n^2/2! + ...
  double e(int n) {
    int x = 1; // x stands for n^i
    double res = 0; // total of the e^n
    for(int i = 0; i < 10; i++) {
      res += x / factorial(i);
      x = x * n;
    }
    return res;
  }
  // The n in factorial function is different from the n in e function
  ```
  
### Implementation Hiding
- Hides how a task is performed
- Caller only needs to know what function does
- Reduces information needed between programmers
- Allows implementation changes without affecting callers
- Example:
  ```java
  double sinc(double x) {
    return Math.sin(x) / x;
  } 
  // Unnormalized signal processing function
  // sinc function sinc(x) = sin(x)/x
  // Caller only needs to know what sinc does, not the implementation details
  ```

### Code Reuse
- Reduces repeated code through parameterization
- Makes code more succinct and readable
- Reduces places that need modification when code evolves
- Decreases chance of introducing bugs
- Example:
  ```java
  double distance(double x1, double y1, double x2, double y2) {
    double xCoordinates = Math.pow((x2 - x1), 2);
    double yCoordinates = Math.pow((y2 - y1), 2);
    return Math.sqrt(xCoordinates + yCoordinates);
  }
  
  boolean isEquilateral(double x1, double y1, double x2, double y2, double x3, double y3) {
    return distance(x1, y1, x2, y2) == distance(x1, y1, x3, y3)
        && distance(x1, y1, x2, y2) == distance(x2, y2, x3, y3); 
  }
  ```

## Abstraction Barrier
- Separates code that calls function from code that implements function
- Divides programmer roles:
    - Implementer: provides implementation
    - Client: uses the function
- Enforces separation of concerns
- Allows implementation changes without affecting client code
- Protects implementation details from client
- The separation allows collaborative programming when people work on the same codebase
- Example:
  ```java
  public class MathSquare {
    private int square(int x) {
      return x * x;
    } // private function for implementer to hide the logic

    public int useSquare(int x) {
      return square(x);
    } // public function for client usage
  }

  public class Main {
    public static void main(String[] args) {
      MathSquare sq = new MathSquare();
      int result = sq.useSquare(5);
      System.out.println("The result is: " + result);  
    }
  }
  ```

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
