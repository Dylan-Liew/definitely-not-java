# Nested Classes Summary

## Types of Nested Classes
1. Inner Classes
2. Static Nested Classes
3. Local Classes
4. Anonymous Classes

## Inner Classes
- Has access to all outer class members
- Requires instance of outer class
- Example:
  ```java
  class Outer {
    private int x;
    static int y;
    
    class Inner {
      private int x;

      void method() {
        A1.this.x = 1; // instance field
        A1.y = 1; //static field
        this.x // field in inner class
      }
    }
  }
  ```

## Static Nested Classes
- Declared with static modifier
- Cannot access instance members of outer class
- Example:
  ```java
  class Outer {
    private static int x;
    
    static class StaticNested {
      void method() {
        x = 1;  // can access static members
      }
    }
  }
  ```

## Local Classes
- Defined inside methods
- Can access local variables (must be final/effectively final)
- Example:
  ```java
  void method() {
    final int x = 1;
    class Local {
      void innerMethod() {
        System.out.println(x);  // can access final local vars
      }
    }
  }
  ```

## Anonymous Classes
- Class definition and instantiation combined
- Often used for interfaces/abstract classes
- Example - Implementing an Interface
  ```java
  interface A {
    void show();
  }

  public class Test {
    public static void main(String[] args) {
      A obj = new A() {
        public void show() {
          System.out.println("Hello from anonymous class");
        }
      };
      obj.show();
    }
  }
  ```

- Example - Extending a Class
  ```java
  class Animal {
    void makeSound() {
      System.out.println("Some sound");
    }
  }

  public class Test {
    public static void main(String[] args) {
      Animal dog = new Animal() {
        void makeSound() {
          System.out.println("Bark");
        }
      };
      dog.makeSound();
    }
  }
  ```

- Example - Generic Types
  ```java
  abstract class Generic<T> {
    abstract void display(T value);
  }

  public class Test {
    public static void main(String[] args) {
      Generic<Integer> obj = new Generic<>() {
        void display(Integer value) {
          System.out.println("Value: " + value);
        }
      };
      obj.display(100);
    }
  }
  ```

## Variable Capture
- Local and anonymous classes can capture variables
- Variables must be final or effectively final
- Example:
  ```java
  void method() {
    final int x = 1;
    Runnable r = new Runnable() {
      @Override
      public void run() {
        System.out.println(x);  // captures x
      }
    };
  }
  ```

## Best Practices
- Use static nested classes when possible
- Keep inner classes small and focused
- Consider lambda expressions instead of anonymous classes
- Be careful with variable capture
- Document nested class relationships
- Use nested classes for encapsulation
