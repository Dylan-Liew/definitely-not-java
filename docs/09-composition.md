# Composition Summary

## Composition Concept
- Building complex classes using simpler classes
- Models "HAS-A" relationship between classes
- Example:
  ```java
  class Circle {
    private Point c;   // Circle HAS-A Point
    private double r;
  }
  ```

## Benefits of Composition
- Builds layers of abstraction
- Encapsulates implementation details
- Makes code more modular
- Allows reuse of existing classes
- Simplifies complex class implementations

## Example of Composition
```java
// Building up from Point to Circle to Cylinder
class Point {
  private double x;
  private double y;
}

class Circle {
  private Point center; // Circle HAS-A Point
  private double radius;
}

class Cylinder {
  private Circle base; // Cylinder HAS-A Circle
  private double height;
}
```

## Reference Sharing Issues (Aliasing)
- Objects can share references to components
- Changes to shared components affect all objects
- Example of problematic sharing:
  ```java
  Point p = new Point(0, 0);
  Circle c1 = new Circle(p, 1);
  Circle c2 = new Circle(p, 4);
  p.moveTo(1, 1);  // affects both c1 and c2
  ```

## Solutions to Reference Sharing
1. Avoid Sharing References
   ```java
   Point p1 = new Point(0, 0);
   Circle c1 = new Circle(p1, 1);
   Point p2 = new Point(0, 0);
   Circle c2 = new Circle(p2, 4);
   ```

2. Create Defensive Copies
   ```java
   // Defensive copy ensures that external changes to `c` do not affect Circle
   class Circle {
     public Circle(Point c, double r) {
       this.c = new Point(c.getX(), c.getY());
       this.r = r;
     }
   }
   ```

## Trade-offs
- Avoiding sharing:
    - Pros: Prevents unintended modifications
    - Cons: Uses more memory, less efficient
- Sharing references:
    - Pros: Memory efficient
    - Cons: Can lead to bugs, harder to maintain

## Best Practices
- Consider carefully whether to share references
- Document sharing behavior clearly
- Use defensive copying when appropriate
- Consider making objects immutable
- Design classes to prevent accidental sharing


> Notes:
- Composition over inheritance principle
    - Composition offers better flexibility, looser coupling and encapsulation
        - Example:
          ```java
          class Order {
            // private composition
            private Payment payment;

            public boolean isPaid() {
              return payment != null && payment.status().equals("SUCCESS");
            }
          }
          ```
    - Inheritance ties classes rigidly and breaks encapsulation by exposing superclass internals

- Polymorphic composition
    - Compose a class using interfaces or abstract classes
    - Allow dynamic behavior injection for different implementations
    - Example
      ```java
      // Different types of Engine can be implemented for different Car
      interface Engine {
        void start();
      }

      class PetrolEngine implements Engine {
        @Override
        public void start() {
          System.out.println("Petrol engine starting...");
        }
      }
      
      class Car {
        private Engine engine;

        public Car(Engine engine) {
          this.engine = engine;
        }

        public void drive() {
          engine.start();
        }
      }
      ```

- Decorator pattern
    - A structural design pattern
    - Allows attaching new responsibilities to an object dynamically
    - Adds behavior at runtime
    - Example:
      ```java
      interface Coffee {
        double cost();
      }

      class BasicCoffee implements Coffee {
        public double cost() { return 2.0; }
      }

      class MilkDecorator implements Coffee {
        private final Coffee base; // Composition
        public MilkDecorator(Coffee base) {
          this.base = base;
        }
        public double cost() {
          return base.cost() + 0.5;
        }
      }
      ```

  