# Dynamic Binding Summary

## Method Invocation Process
- Two-step process:
    1. Compile-time: Determine method descriptor
    2. Runtime: Find and execute actual method

## Compile-Time Step
- Uses compile-time type of target
- Searches for methods in target's class and supertypes
- Checks method signature compatibility
- Selects most specific compatible method
- Example:
  ```java
  Shape s = new Circle();
  s.getArea();  // compile-time type is Shape
  ```

## Method Specificity
- Method M is more specific than N if:
    - M's arguments can be passed to N
    - N's arguments cannot always be passed to M
- Example:
  ```java
  void foo(Circle c) { }     // more specific
  void foo(Shape s) { }      // less specific
  ```

## Runtime Step
- Uses runtime type of target
- Searches for method starting from runtime type
- Moves up class hierarchy if not found
- Executes first matching method found
- Example:
  ```java
  Shape s = new Circle();
  s.getArea();  // runtime type is Circle, calls Circle's getArea
  ```

## Method Search Order
1. Check runtime type class
2. If not found, check parent class
3. Continue up hierarchy to Object
4. Use first matching method found
- Example:
  ```java
  class A { void foo() { } }
  class B extends A { void foo() { } }
  class C extends B { }
  // C object calls B's foo()
  ```

## Class Methods (Static)
- No dynamic binding
- Resolved at compile time
- Based on compile-time type only
- Example:
  ```java
  Shape s = new Circle();
  s.staticMethod();  // calls Shape's method regardless of runtime type
  ```

## Best Practices
- Understand compile-time vs runtime types
- Be aware of method resolution rules
- Document overridden method behavior
- Use @Override to clarify intentions
- Consider making methods final if overriding not intended
