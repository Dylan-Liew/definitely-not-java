# Type Inference Summary

## Type Inference Concept
- Compiler determines types automatically
- Reduces verbosity in generic code
- Based on context and type constraints
- Example:
  ```java
  // Without type inference
  List<String> list = new ArrayList<String>();
  
  // With type inference
  List<String> list = new ArrayList<>();  // diamond operator
  ```

## Diamond Operator
- Used in constructor calls
- Infers type from declaration
- Example:
  ```java
  Map<String, List<Integer>> map = new HashMap<>();
  Pair<Double, String> pair = new Pair<>();
  ```

## Method Type Inference
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

## Target Typing
- Uses assignment context for inference
- Considers variable type
- Example:
  ```java
  List<String> strings = Collections.emptyList();  // infers List<String>
  void process(List<Integer> ints) { }
  process(Collections.emptyList());  // infers List<Integer>
  ```

## Type Inference Rules
- Most specific type is chosen
- Must satisfy all constraints
- Example:
  ```java
  // T must be supertype of both String and Integer
  <T> void addToList(List<T> list, T item1, T item2) { }
  List<Object> list = new ArrayList<>();
  addToList(list, "hello", 42);  // T inferred as Object
  ```

## Best Practices
- Use diamond operator
- Let compiler infer types when clear
- Provide explicit types when needed
- Test inference with edge cases
- Document when inference is complex
- Consider readability vs brevity
