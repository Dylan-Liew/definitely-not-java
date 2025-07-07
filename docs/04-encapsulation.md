# Encapsulation Summary

## Composite Data Type
- Groups primitive types together into new types
- Gives the group a name for future reference
- Abstracts away implementation details
- Examples: complex numbers, 2D points, vectors

## Class and Object
- Class: Bundles composite data type with associated functions
- Uses class abstraction as a tool to define composite data type and add methods that operate on the data (fields)
- Components:
    - Fields (also called states, attributes, or properties)
    - Methods (functions that operate on the fields)
- Objects: Instances of a class
- Example:
  ```java
  class Circle {
    private double x;
    private double y;
    private double r;

    double getArea() {
      return 3.141592653589793 * r * r;
    }
  }
  ```

## Encapsulation
- Keep all the data (fields) and functions (methods) operating on the data (fields) related to a composite data type together within an abstraction barrier

## Object Creation and Access
- Objects created using `new` keyword
- Objects as instances of a class:
  - Each object allows the same methods to be called
  - Each object contains the same set of variables of the same types
  - Each object may store different values
- Access fields and methods using dot `.` notation
- Example:
  ```java
  Circle c = new Circle();
  c.r = 10;
  c.getArea();
  ```

## Object-Oriented Programming Principles
- Program consists of interacting objects
- Objects contain:
    - Data (fields)
    - Operations (methods AKA functions)
- Natural modeling of real-world objects
- Models:
    - Nouns as classes/objects
    - Properties/relationships as fields
    - Actions as methods

## Reference Types in Java
- Classes are reference types
- Variables store references to objects, not objects themselves
- Multiple variables can reference same object
- Example of sharing:
  ```java
  Circle c1 = new Circle();
  Circle c2 = c1;  // c1 and c2 share same object
  c1.r = 10;       // affects both c1 and c2
  ```

## Special Reference Value: null
- Default value for uninitialized reference variables
- Attempting to use null reference causes NullPointerException
- Must initialize reference variables before use
- Example:
  ```java
  Circle c1;           // c1 is null
  c1.r = 10;          // NullPointerException
  ```

## Good Design Practices
- Keep related data and methods together
- Hide implementation details
- Model real-world relationships appropriately
- Initialize references before use
- Be careful with shared references
