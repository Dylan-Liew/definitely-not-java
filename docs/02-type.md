# Variable and Type Summary

## Data Abstraction: Variable
- A variable is a named abstraction for accessing a value stored in memory
- Primitive variables store actual values and are independent
- Reference variables store memory addresses and can share objects in memory
- Use the variable name to access the value in that memory location
- Pointer/Rerference to the variable to refer to the address of the location 

## Types
- Assign a type to a variable to manage program complexity
- Communicate data type information to readers
- Allow compiler to check for valid operations
- Determine how operations behave
- Example (Java and JavaScript): 
    - variables x and y, storing the values 4 and 5 respectively
    - String + String concatenates: 
        String x + String y, the ouput is 45
    - Integer + Integer adds: 
        int x + int y, the output is 9
    - Integer + String concatenates:
        int x + String y, x is converted into a string, the output is 45
    

## Static vs Dynamic Typing
- Dynamic Typing (e.g., Python, JavaScript)
    - Variables can hold different types
    - Type checking done at runtime
    - Type associated with values
    - Example: `x = 1; x = "hello"` is valid

- Static Typing (e.g., Java)
    - Variables must declare type
    - Type checking done at compile time
    - Type cannot change after declaration
    - Type is attached to the variable to only store values of that particular type
    - Example: `int x = 1; x = "hello"` is invalid

## Strong vs Weak Typing
- It is about a spectrum of "strength" between the typing discipline of a language
- Strong Typing
    - Enforces strict type rules
    - Ensures type safety
    - Prevents implicit type conversions
    - Example: Java prevents casting string to int

- Weak Typing
    - More permissive with type rules
    - Allows implicit type conversions
    - Example: C allows casting between unrelated types

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
- bits refer to the range of values a type can represent
- Use suffix `L` to denote that a value is expected to be of `long` type instead of `int` type
- A floating-point constant is treated as type `double`, a suffix `f` is needed to indicate that it is a `float` type

## Subtyping
- Defines relationship between types where one type can substitute another, T <: S
    - A piece of code written for variables of type S can also be used on variables of type T
    - S is a supertype of T
- Properties:
    - Reflexive: S <: S (a subtype of itself)
    - Transitive: If S <: T and T <: U, then S <: U
    - Anti-symmetric: If S <: T and T <: S, then S = T

## Java Primitive Type Hierarchy
- Subtype relationships:
    - `byte` <: `short` <: `int` <: `long` <: `float` <: `double`
    - `char` <: `int`
- Java Widening Type conversion allows putting a value of type T into a variable of type S if T <: S
- Example:
    ```
    double d = 5.0; // assign 5.0 to d :: double 
    int i = 5; // assign 5 to i :: int
    d = i; // assign i to d (valid, int <: double)
    i = d; // assign d to i (invalid, double </: int)