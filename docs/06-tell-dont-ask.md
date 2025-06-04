# Tell, Don't Ask Summary

## Accessors and Mutators
- Accessor (getter): Methods to retrieve field values
- Mutator (setter): Methods to modify field values
- Example:
  ```java
  class Circle {
    private double r;
    
    public double getR() {     // accessor
      return this.r;
    }
    
    public void setR(double r) { // mutator
      this.r = r;
    }
  }
  ```

## Accessor/Mutator vs Public Fields
### Advantages over public fields:
- Adds layer of abstraction
- Can rename fields without affecting clients
- Can add validation in mutators
- Can control access to fields
- Example with validation:
  ```java
  public void setR(double r) {
    if (r > 0) {
      this.r = r;
    }
  }
  ```

## Problems with Accessors/Mutators
- Can leak implementation details
- Creates coupling between client and class
- Makes code harder to maintain
- Example of coupling:
  ```java
  // Client code depends on internal representation
  double cX = c.getX();
  double cY = c.getY();
  double r = c.getR();
  boolean isInCircle = ((x - cX) * (x - cX) + 
                       (y - cY) * (y - cY)) <= r * r;
  ```

## Tell, Don't Ask Principle
- Tell objects what to do
- Don't ask for internal state
- Let objects perform their own operations
- Better example:
  ```java
  boolean isInCircle = c.contains(x, y);
  ```

## Benefits of Tell, Don't Ask
- Maintains encapsulation
- Reduces coupling between classes
- Makes code more maintainable
- Keeps related computations together
- Allows implementation changes without affecting clients

## Guidelines
- Tasks performed only on class fields should be in that class
- Avoid getters/setters unless absolutely necessary
- Think in terms of object responsibilities
- Focus on object behavior rather than state
- Design methods around what objects should do
