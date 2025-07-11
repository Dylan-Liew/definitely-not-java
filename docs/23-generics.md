# Generics Summary

## Generic Types Concept
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

## Type Parameters
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

## Parameterized Type
- A concrete type created by specifying actual types for generic parameters
- Replaces generic type parameters with real types
- Creates type-safe class instances
- Example:
  ```java
  // This is a generic type (not parameterized yet):
  class Array<T> {    // T is just a placeholder
    private T[] elements;
  }
  
  // These are parameterized types:
  Array<String> words = new Array<>();     // T becomes String
  class StringArray extends Array<String> { } // Array<T> is instantiated as Array<String>

  // Invalid parameterized type examples:
  // class Array<String> { }    // ERROR: Cannot use concrete type in class definition
  // Array<int> numbers;        // ERROR: Cannot use primitive types
  // Array<T> generic;          // ERROR: T is not defined in this context
  ```


## Bounded Type Parameters
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

## Generic Methods
- Methods with their own type parameters
- Type parameter before return type
- Example:
  ```java
  public static <T> void printArray(T[] array) {
    for (T element : array) {
      System.out.println(element);
    }
  }
  ```

## Type Inference
- Java can infer type arguments
- Diamond operator <> for constructors
- Example:
  ```java
  List<String> list = new ArrayList<>();  // type inferred
  Box<Integer> box = new Box<>();         // type inferred
  ```

## Generic Type Restrictions
- Cannot create arrays of generic types
- Cannot create generic exceptions
- Cannot use primitives directly
- Example:
  ```java
  // Not allowed:
  T[] array = new T[10];  // compile error
  
  // Use this instead:
  T[] array = (T[]) new Object[10];
  ```

## Best Practices
- Use generics for type safety
- Prefer bounded wildcards for flexibility
- Document type parameter meanings
- Keep type parameter names meaningful
- Use generic collections over raw types
- Consider type erasure implications
