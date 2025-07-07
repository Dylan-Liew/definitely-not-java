# Variable and Type Summary

## Data Abstraction: Variable
- Variables are named abstractions for accessing values in memory
- Primitive variables store actual values and are independent
- Reference variables store memory addresses and can share objects in memory
- You use the variable name to access the value

## Types
- Manage program complexity
- Communicate data type information to readers
- Allow compiler to check for valid operations
- Determine how operations behave
- Operation Examples:

    ```
    String x = "4";
    String y = "5";
    String result1 = x + y;  // "45" (concatenation)

    int x = 4;
    int y = 5;
    int result2 = x + y;     // 9 (addition)

    int x = 4;
    String y = "5";
    String result3 = x + y;  // "45" (int converted to String, then concatenated)
    ```

## Static vs Dynamic Typing
- Dynamic Typing (e.g., Python, JavaScript)
    - Variables can hold different types
    - Type checking done at runtime
    - Type associated with values
    - Example: `x = 1; x = "hello"` is valid

- Static Typing (e.g., Java)
    - Variables must declare their type at compile time
    - Type checking done at compile time
    - Variable type cannot change after declaration
    - Types are attached to variables to restrict stored value types
    - Example: `int x = 1; x = "hello";` is invalid (compile error)

## Strong vs Weak Typing
- Represents a spectrum of "strength" in a language's typing discipline
- Strong Typing
    - Enforces strict type rules
    - Ensures type safety at runtime
    - Prevents unsafe implicit type conversions
    - Example: Java prevents automatic conversion from String to int
- Weak Typing
    - More permissive with type rules
    - Allows potentially unsafe implicit type conversions
    - Example: C allows casting between unrelated pointer types


## Java Primitive Types
- Boolean: `boolean` (1 bit)
- Character: `char` (16 bits)
- Integral Types:
    - `byte` (8 bits)
    - `short` (16 bits)
    - `int` (32 bits)
    - `long` (64 bits)
- Floating-Point:
    - `float` (32 bits)
    - `double` (64 bits)
- Bit sizes determine the range of values a type can represent
- Use suffix `L` for long literals: `long x = 100L;`
- Floating-point literals default to `double`; use suffix `f` for float: `float x = 3.14f;`


## Subtyping
- Defines when one type can substitute another: T <: S (T is subtype of S)
    - Code written for variables of type S can safely use variables of type T
    - S is a supertype of T, T is a subtype of S
- Properties:
    - Reflexive: S <: S (subtype of itself)
    - Transitive: If S <: T and T <: U, then S <: U
    - Anti-symmetric: If S <: T and T <: S, then S = T

## Java Primitive Type Hierarchy
- Subtype relationships:
    - `byte` <: `short` <: `int` <: `long` <: `float` <: `double`
    - `char` <: `int`
- Widening conversions allow assigning value of type T to variable of type S if T <: S
- **Example:**
    ```java
    double d = 5.0; // assign 5.0 to d (double)
    int i = 5;      // assign 5 to i (int)
    d = i;          // valid: int <: double (widening conversion)
    i = d;          // invalid: double ≮: int (would require narrowing cast)
    ```
    