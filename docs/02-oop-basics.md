# Object-Oriented Programming Basics

## Encapsulation

### Class and Object Concept
- Class: Bundles composite data type with associated functions
- Components:
    - Fields (states, attributes, or properties)
    - Methods (functions that operate on the fields)
- Objects: Instances of a class
- Example:
  ```java
  class Circle {
    private double x;
    private double y;
    private double r;

    double getArea() {
      return Math.PI * r * r;
    }
  }
  ```

### Reference Types in Java
- Classes are reference types
- Variables store references to objects, not objects themselves
- Multiple variables can reference same object
- Special reference value: `null` indicates no object reference
- NullPointerException occurs when attempting to use null reference

## Information Hiding

### Access Modifiers
- Control access to class members:
    - `private`: Only accessible within the class
    - `public`: Accessible from anywhere
- Access control enforced by compiler
- Example:
  ```java
  class Circle {
    private double x;  // hidden from outside
    private double y;
    private double r;

    public double getArea() {  // accessible from outside
      return Math.PI * r * r;
    }
  }
  ```

### Abstraction Barrier
- Direct access to internal fields breaks abstraction
- Makes code dependent on implementation details
- Changes to implementation can break client code
- Reduces code maintainability

### Constructors
- Special methods to initialize objects
- Same name as class
- No return type
- Called automatically with `new`
- Example:
  ```java
  class Circle {
    private double x;
    private double y;
    private double r;

    public Circle(double x, double y, double r) {
      this.x = x;
      this.y = y;
      this.r = r;
    }
  }
  ```

## Tell, Don't Ask Principle

### Accessor and Mutator Methods
- Accessor (getter): Methods to retrieve field values
- Mutator (setter): Methods to modify field values
- Benefits over public fields:
    - Adds layer of abstraction
    - Can add validation in mutators
    - Can control access to fields

### Principle Explained
- Tell objects what to do
- Don't ask for internal state
- Let objects perform their own operations
- Example:
  ```java
  // Don't do this:
  double cX = c.getX();
  double cY = c.getY();
  double r = c.getR();
  boolean isInCircle = ((x - cX) * (x - cX) + (y - cY) * (y - cY)) <= r * r;
  
  // Do this instead:
  boolean isInCircle = c.contains(x, y);
  ```

### Benefits
- Maintains encapsulation
- Reduces coupling between classes
- Makes code more maintainable
- Keeps related computations together
- Allows implementation changes without affecting clients
