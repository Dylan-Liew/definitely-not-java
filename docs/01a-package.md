# Java Packages

## Package Concept
- Packages group related classes together
- Provide an abstraction barrier for code organization
- Help manage the namespace and avoid naming conflicts
- Enable access control between different parts of code

## Package Naming Convention
- Hierarchical dot notation (e.g., `com.google.common.math`, `java.io`)
- Usually follows reverse domain name of the organization
  ```
  com.company.project.module
  ```
- Prevents package name collisions across different organizations

## Package Structure and File System
- Java maps package names to directory hierarchy
- Class `a.b.C` is looked for in path `a/b/C.class`
- Example:
  ```
  package com.example.project;
  
  public class MyClass { ... }

  // This class would be stored in: com/example/project/MyClass.class
  ```

## Default Package
- Classes without a package declaration belong to the "default" package
- All classes in the same directory without package declarations share this namespace

## Package Access Control
| Modifier       | Class | Package | Subclass (same pkg) | Subclass (diff pkg) | World |
|---------------|:-----:|:-------:|:-------------------:|:-------------------:|:-----:|
| **public**    | ✅    | ✅      | ✅                  | ✅                  | ✅    |
| **protected** | ✅    | ✅      | ✅                  | ✅                  | ❌    |
| *(no modifier)* | ✅  | ✅      | ✅                  | ❌                  | ❌    |
| **private**   | ✅    | ❌      | ❌                  | ❌                  | ❌    |


## Example of Protected Access
```java
// In file A.java (package com.example)
package com.example;

public class A {
    protected int x;  // protected data field
}
```

```java
// In file B.java (package com.example)
package com.example;

public class B {
    public void accessX() {
        A a = new A();
        a.x = 10;  // Accessible: same package
    }
}
```

```java
// In file C.java (package com.example.other)
package com.example.other;

import com.example.A;

public class C extends A {
    public void accessX() {
        x = 20;  // Accessible: subclass from different package
    }
}
```

```java
// In file D.java (package com.example.other)
package com.example.other;

import com.example.A;

public class D {
    public void accessX() {
        A a = new A();
        // a.x = 30;  // ERROR: Cannot access protected field from unrelated class
    }
}
```

## Creating and Using Packages
- Declare package as the first line in your Java file:
  ```java
  package cs2030s.fp;
  
  public interface BooleanCondition<T> {
      boolean test(T t);
  }
  ```

- To use classes from other packages:
  ```java
  // Option 1: Full qualification
  cs2030s.fp.BooleanCondition<Integer> isEven = x -> x % 2 == 0;
  
  // Option 2: Import and use
  import cs2030s.fp.BooleanCondition;
  BooleanCondition<Integer> isEven = x -> x % 2 == 0;
  ```

## Best Practices
- Organize related classes in the same package
- Use hierarchical packages for large projects
- Always declare packages in production code
- Use meaningful package names that reflect code purpose
- Keep package structure aligned with project architecture
