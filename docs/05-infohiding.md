# Information Hiding Summary

## Breaking Abstraction Barrier
- Direct access to internal fields breaks abstraction
- Example problem:
  ```java
  c.r = 10;  // directly modifying radius
  ```
- Makes code dependent on implementation details
- Changes to implementation can break client code
- Reduces code maintainability

## Access Modifiers
- Java provides access control through modifiers:
    - `private`: Only accessible within the class
    - `public`: Accessible from anywhere
- Default access (no modifier) exists but not covered
- Access control enforced by compiler
- Example:
  ```java
  class Circle {
    private double x;  // hidden from outside
    private double y;
    private double r;

    public double getArea() {  // accessible from outside
      return 3.141592653589793 * r * r;
    }
  }
  ```

## Access Modifier Summary Table
| Access From | private | public |
|-------------|---------|---------|
| Inside class | Yes | Yes |
| Outside class | No | Yes |

## Constructors
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

## Default Constructor
- Provided by Java if no constructor defined
- Takes no parameters
- Empty body
- Example:
  ```java
  Circle() {
  }
  ```
- Not provided if any constructor is defined

## The `this` Keyword
- Reference to current object
- Used to:
    - Distinguish between parameters and fields
    - Access object's own members
- Example:
  ```java
  this.x = x;  // field x = parameter x
  ```
- Makes code more explicit and readable
- Helps avoid naming conflicts
