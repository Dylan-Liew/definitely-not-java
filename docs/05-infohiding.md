# Information Hiding Summary

## Breaking Abstraction Barrier
- Direct access to internal fields breaks abstraction
- Example problem:
  ```java
  Circle c = new Circle();
  c.r = 10;  // directly modifying radius
  ```
- Makes code dependent on implementation details
- Changes to implementation can break client code
- Reduces code maintainability
- As an implementer, expose as few fields/methods as possible
- As a client, follow the behavior as stated in the specification such as `Java API`

## Access Modifiers
- Java provides access control through modifiers:
    - `private`: Only accessible within the class
    - `public`: Accessible from anywhere
- Default access (no modifier) exists but not covered; it is package-private
- Access control enforced by compiler at compile time
- Different objects of the same class can access each other's private fields and methods within the class
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

  // Testing
  Circle c = new Circle();
  c.r = 10; // compilation error
  ```

## Access Modifier Summary Table
| Access From | private | public |
|-------------|---------|---------|
| Inside class | Yes | Yes |
| Outside class | No | Yes |

## Constructors
- Behavior of a constructor:
    - Allocate memory for all fields and assign the reference to `this`
    - Invoke the constructor function, passing the keyword `this` implicitly
    - Once the constructor is done, return the reference pointed to by `this`
- Special methods for clients to initialize objects
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
- Provided by Java if no constructor is defined
- Takes no parameters
- Empty body
- Example:
  ```java
  Circle() {
  } // no parameters and no code written for the body
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
