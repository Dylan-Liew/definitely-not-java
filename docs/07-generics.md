# Generics

## Generic Types

### Generic Types Concept
- Allow type parameters in class/interface definitions
- Enable type-safe collections/operations
- Prevent runtime type errors
- Example:
  ```java
  class Box<T> {
    private T item;
    
    public void put(T item) {
      this.item = item;
    }
    
    public T get() {
      return item;
    }
  }
  ```

### Type Parameters
- Commonly used letters:
    - T for type
    - E for element
    - K for key
    - V for value
    - S,U,V for multiple types
- Example:
  ```java
  class Pair<K,V> {
    private K key;
    private V value;
  }
  ```

### Bounded Type Parameters
- Restrict type parameters to certain types
- Use extends keyword
- Can bound to class or interface
- Example:
  ```java
  class NumberBox<T extends Number> {
    private T number;
    
    public double getValue() {
      return number.doubleValue();  // OK because T extends Number
    }
  }
  ```

## Type Erasure

### Type Erasure Concept
- Java's implementation of generics
- Removes type parameters at compile time
- Replaces with Object or bounds
- Maintains backward compatibility
- Example:
  ```java
  // Before erasure
  class Box<T> {
    private T item;
  }
  
  // After erasure
  class Box {
    private Object item;  // T replaced with Object
  }
  ```

### Erasure with Bounds
- Bounded type replaced with bound
- Example:
  ```java
  // Before erasure
  class NumberBox<T extends Number> {
    private T number;
  }
  
  // After erasure
  class NumberBox {
    private Number number;  // T replaced with Number
  }
  ```

### Generic Method Type Inference
- Infers type arguments for generic methods
- Based on:
    - Method arguments
    - Return type context
    - Type constraints
- Example:
  ```java
  static <T> List<T> asList(T... elements) {
    return Arrays.asList(elements);
  }
  
  List<String> list = asList("a", "b", "c");  // T inferred as String
  ```

## Wildcards

### Wildcard Types
- Represented by `?`
- Three types of wildcards:
    1. Upper Bounded: `<? extends Type>`
    2. Lower Bounded: `<? super Type>`
    3. Unbounded: `<?>`

### PECS Principle
- Producer Extends, Consumer Super
- Use extends for input (reading)
- Use super for output (writing)
- Example:
  ```java
  // Producer (extends) - reading from source
  void copyFromSource(List<? extends Shape> source) {
    Shape s = source.get(0);  // OK
  }
  
  // Consumer (super) - writing to dest
  void copyToDest(List<? super Circle> dest) {
    dest.add(new Circle());  // OK
  }
  ```

### Generic Restrictions and Best Practices
- Cannot create arrays of generic types
- Cannot create generic exceptions
- Cannot use primitives directly
- Use wildcards appropriately
- Document generic behavior
- Consider type erasure implications
