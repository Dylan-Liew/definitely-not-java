# Exceptions Summary

## Exception Handling Basics
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

## Types of Exceptions
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

## Throwing Exceptions
- Use throw keyword
- Can throw new exceptions
- Must declare checked exceptions
- Example:
  ```java
  public void readFile(String fileName) throws IOException {
    throw new IOException("File not found");
  }
  ```

## Creating Custom Exceptions
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

## Exception Handling Best Practices
- Only catch exceptions you can handle
- Don't catch and ignore exceptions
- Clean up resources in finally block
- Use specific exception types
- Document exceptions in Javadoc
- Don't use exceptions for flow control

## Common Mistakes to Avoid
- Empty catch blocks
- Catching Exception (too general)
- Not cleaning up resources
- Throwing wrong exception type
- Example of bad practice:
  ```java
  try {
    // code
  } catch (Exception e) {
    // empty catch block - DON'T DO THIS
  }
  ```

## Try-with-Resources
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