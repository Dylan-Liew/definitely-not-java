# Liskov Substitution Principle Summary

## LSP Definition
- Programmer's responsibility to follow the LSP
- Subtype must be completely substitutable for its supertype
- A subclass should not break the expectations set by the superclass.
- **Formal Definition**: Let φ(x) be a property provable about objects x of type T. Then φ(y) should be true for objects y of type S where S <: T
- A subclass should pass all test cases of its superclass
- Example:
  ```java
  // Superclass Restaurant
  public class Restaurant {
    public static final int OPENING_HOUR = 1200;
    public static final int CLOSING_HOUR = 2200;

    public boolean canMakeReservation(int time) {
      if (time <= CLOSING_HOUR && time >= OPENING_HOUR) {
        return true;
      }
      return false;
    }
  }
  ```
  ```java
  // Subclass LunchRestaurant
  public class LunchRestaurant extends Restaurant {
    private final int peakHourStart = 1200;
    private final int peakHourEnd = 1400;

    @Override
    public boolean canMakeReservation(int time) {
      if (time <= peakHourEnd && time >= peakHourStart) {
        return false;
      } else if (time <= CLOSING_HOUR && time >= OPENING_HOUR) {
        return true;
      }
      return false;
    }
  }
  ```
  ```java
  // Subclass LunchRestaurant
  public class DigitalReadyRestaurant extends Restaurant {

    @Override
    public boolean canMakeReservation(int time) {
      return true;
    }
  }
  ```
  ```java
  Restaurant r = new LunchRestaurant();
  r.canMakeReservation(1200) == true; // Is false, therefore test fails
  r.canMakeReservation(2200) == true; // Is true, therefore test passes
  // LunchRestaurant violates LSP

  Restaurant r = new DigitalReadyRestaurant();
  r.canMakeReservation(1200) == true; // Is true, therefore test passes
  r.canMakeReservation(2200) == true; // Is true, therefore test passes
  // DigitalReadyRestaurant is substitutable for Restaurant
  ```
  
## Preventing Inheritance
- Use `final` keyword to prevent inheritance
- Example:
```java
final class String {  // Cannot be inherited
  // implementation
}
```

## Preventing Method Overriding
- Use `final` keyword on methods
- Prevents subclasses from changing behavior
- Example:
```java
class Circle {
  final double getArea() {  // Cannot be overridden
    return Math.PI * r * r;
  }
}
```
## Preventing Field Re-assignment
- Use `final` keyword on methods
- Prevents re-assignment to the field
- Example:
```java
class Queue {
  final static int id = 1;
}
```

## Best Practices
- Design inheritance hierarchies carefully
- Document expected behavior and constraints
- Use `final` when inheritance not intended
- Test subclasses against superclass contracts
- Consider composition over inheritance
- Make classes immutable when possible
- Write clear specifications for methods

