# Method Overriding Summary

## Object Class
- Every class implicitly inherits from `Object`
- `Object` provides common methods:
    - `equals(Object obj)`: Check equality
    - `toString()`: String representation
    - `hashCode()`: Hash value
    - Others like `clone()`, `finalize()`
    - specific reference: `Object::equals(Object)`
        - The method is defined in class `Object`
        - The method takes one `Object` parameter

## Method Summary
- Method Signature
    - Includes the name of the method and the type of parameters
    - The information captured are:
        - Method name
        - Number of parameters
        - Types of parameters
        - Order of parameters
        - Class name (Optional)
    - Does NOT include:
        - Return type
        - Parameter names
        - Access modifiers

- Method Descriptor
    - Includes everything in the method signature + return type
    - The information captured are:
        - Method name
        - Number of parameters
        - Types of parameters
        - Order of parameters
        - Return type
        - Class name (Optional)

- Class names are included for mentioning a specific implementation
- Exclude the class names to talk about the method regardless of where it is implemented 
- Omit the parameters to talk about all the methods with the given name (C::foo)

| Summary Type   | Without Class Name | With Class Name    |
| -------------- | ------------------ | ------------------ |
| **Signature**  | `foo(B1, B2)`      | `C::foo(B1, B2)`   |
| **Descriptor** | `A foo(B1, B2)`    | `A C::foo(B1, B2)` |

## The `toString` Method
- This method is invoked implicitly during string concatenation and inside `System.out.println(..)`
- Assignment to a String variable does not invoke this method implicitly
- Convert a reference object to a `String` object
- Override this method in other classes to design customised `toString()` method
- Example:
  ```java
  class Person {
    public String toString() {
      return "Dylan";
    }
  }
  ```
  ```java
  Person p = new Person();
  String message = "Name: " + p; // Implicitly call toString()
  ```
  ```java
  Person p = new Person();
  System.out.println(p); // Implicitly call toString()
  ```
  ```java
  Person p = new Person();
  String p2 = p; // Error: incompatible types
                 // toString() is not invoked
                 // Must call p.toString() explicitly
  ```

## Method Overriding
- Subclass provides new implementation of parent's method
- Must have same method descriptor as parent
- Enables polymorphic behavior
- Example:
  ```java
  class Circle {
    @Override
    public String toString() {
      return "Circle with radius " + this.r;
    }
  }
  ```

## Rules for Overriding
- Method must have:
    - Same name
    - Same parameters (number, type, order)
    - Same return type (or covariant for different return type)
    - Same or less restrictive access
- Cannot override:
    - `final` methods
    - `static` methods
    - `private` methods

## @Override Annotation
- Annotation is a hint to the compiler
- Indicates method is meant to override
- Helps catch errors at compile time
- Best practice to always use it
- Example:
  ```java
  @Override  // Compiler checks if parent has this method
  public boolean equals(Object obj) {
    // implementation
  }
  ```

## Using `super` with Overridden Methods
- Access parent class's version using `super`
- Useful when extending behavior
- Example:
  ```java
  @Override
  public String toString() {
    return super.toString() + " (custom info)"; 
  }
  ```

## Common Methods to Override
- `toString()`: String representation
- `equals(Object)`: Object equality
- `hashCode()`: Hash code for hash-based collections
- Example:
  ```java
  @Override
  public boolean equals(Object obj) {
    if (obj instanceof Circle) {
      Circle other = (Circle) obj;
      return this.radius == other.radius;
    }
    return false;
  }
  ```

## Best Practices
- Always use @Override annotation
- Override toString() for debugging
- Override equals() and hashCode() together
- Keep overridden methods consistent with parent class's contract
- Document overridden behavior
