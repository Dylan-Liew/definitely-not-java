# Exceptions and Wrapper Types

## Exception Handling

### Exception Handling Basics
- Mechanism to handle runtime errors
- Uses try-catch-finally blocks
- Allows separation of error handling from main logic
- Example:
  ```java
  try {
    // code that might throw exception
    readFromFile(filename);
  } catch (FileNotFoundException e) {
    // handle the exception
    System.err.println("File not found: " + e.getMessage());
  } finally {
    // cleanup code, always executed
    closeFile();
  }
  ```

### Types of Exceptions
1. Checked Exceptions:
     - Must be declared or caught
     - Extend Exception class
     - Example: IOException

2. Unchecked Exceptions:
     - Don't need to be declared
     - Extend RuntimeException
     - Example: NullPointerException

3. Errors:
     - Serious problems
     - Not meant to be caught
     - Example: OutOfMemoryError

### Creating Custom Exceptions
- Extend Exception or RuntimeException
- Add constructors and fields as needed
- Example:
  ```java
  class InvalidCircleException extends IllegalArgumentException {
    public InvalidCircleException(String message) {
      super(message);
    }
  }
  ```

### Try-with-Resources
- Automatically closes resources
- For classes implementing AutoCloseable
- Example:
  ```java
  try (FileReader reader = new FileReader(file)) {
    // use reader
  } catch (IOException e) {
    // handle exception
  }
  // reader automatically closed
  ```

## Wrapper Classes

### Wrapper Class Concept
- Classes that encapsulate primitive types
- Convert primitives to objects
- Provide utility methods
- Enable use of primitives in generic code
- Example:
  ```java
  Integer i = new Integer(42);  // wraps int
  Double d = new Double(3.14);  // wraps double
  ```

### Java Wrapper Classes
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

### Auto-boxing and Unboxing
- Auto-boxing: Automatic primitive to wrapper conversion
- Unboxing: Automatic wrapper to primitive conversion
- Example:
  ```java
  Integer i = 42;    // auto-boxing
  int n = i;         // unboxing
  ```

### Utility Methods
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

## Type Casting and Variance

### Run-Time Class Mismatch
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

### Safe Casting Practices
- Always check type before casting
- Use instanceof operator
- Example:
  ```java
  if (shape instanceof Circle) {
    Circle c = (Circle) shape;  // safe cast
    // use c
  }
  ```

### Java Array Covariance
- Arrays are covariant in Java
- Can lead to runtime errors
- Example:
  ```java
  Integer[] intArray = new Integer[2];
  Object[] objArray = intArray;        // OK due to covariance
  objArray[0] = "Hello";              // Runtime error!
  ```
