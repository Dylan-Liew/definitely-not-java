# Wildcards Summary

## Wildcard Types
- Represented by `?`
- Three types of wildcards:
    1. Upper Bounded: `<? extends Type>`
    2. Lower Bounded: `<? super Type>`
    3. Unbounded: `<?>`

## Upper Bounded Wildcards
- Accepts type and its subtypes
- Used for reading from structure
- Example:
  ```java
  void printShapes(List<? extends Shape> shapes) {
    for (Shape s : shapes) {
      System.out.println(s.getArea());
    }
  }
  ```

## Lower Bounded Wildcards
- Accepts type and its supertypes
- Used for writing to structure
- Example:
  ```java
  void addCircles(List<? super Circle> list) {
    list.add(new Circle());
    list.add(new Circle(1.0));
  }
  ```

## PECS Principle
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

## Unbounded Wildcards
- Represented by `<?>`
- Used when actual type doesn't matter
- Example:
  ```java
  void printList(List<?> list) {
    for (Object o : list) {
      System.out.println(o);
    }
  }
  ```

## Wildcard Capture
- Compiler captures unknown type
- Used in helper methods
- Example:
  ```java
  public void swap(List<?> list, int i, int j) {
    swapHelper(list, i, j);  // helper method
  }
  
  private <T> void swapHelper(List<T> list, int i, int j) {
    T temp = list.get(i);
    list.set(i, list.get(j));
    list.set(j, temp);
  }
  ```

## Best Practices
- Use PECS principle
- Prefer wildcards over type parameters
- Use unbounded wildcards for Object methods
- Document wildcard usage
- Consider readability vs flexibility
- Test with different type hierarchies
