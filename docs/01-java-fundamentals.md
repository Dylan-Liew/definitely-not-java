# Java Fundamentals

## Java Program and Compiler

### Software Programs
- A program is a collection of data variables and instructions
- Programs are written in programming languages using keywords, symbols, and names
- Programming languages provide higher level abstraction for complex instructions

### Java Execution
- Java uses a hybrid approach: "Write once, run anywhere" principle
- Two ways to run Java programs:
    1. Compile to bytecode first, then interpret/compile via JVM
    2. Direct interpretation using Java interpreter
- Java Virtual Machine (JVM):
    - Platform-specific runtime environment
    - Converts bytecode to machine code using Just-In-Time (JIT) compilation
    - Handles memory management and garbage collection
    - Provides platform independence through abstraction layer

### Compilation Process
- Java compiler (`javac`) compiles source code (.java) to bytecode (.class)
- Basic compilation steps:
  ```
  javac Hello.java    # creates Hello.class
  java Hello          # runs the program
  ```
- Compilation phases:
    1. Parsing: Source code to syntax tree
    2. Semantic analysis: Type checking and symbol resolution
    3. Bytecode generation: Platform-independent instructions

## Variable and Type System

### Data Abstraction: Variable
- Variables are named abstractions for accessing values stored in memory
- Primitive variables store actual values and are independent
- Reference variables store memory addresses and can share objects

### Java Type System
- Static typing: Variables must declare type, checked at compile time
- Strong typing: Enforces strict type rules, prevents unsafe conversions
- Types help manage complexity and enable compile-time checking

### Java Primitive Types
- Boolean: `boolean` (1 bit)
- Character: `char` (16 bits)
- Integral Types: `byte` (8 bits), `short` (16 bits), `int` (32 bits), `long` (64 bits)
- Floating-Point: `float` (32 bits), `double` (64 bits)

### Type Relationships
- Subtyping defines when one type can substitute for another (T <: S)
- Primitive conversions: `byte` <: `short` <: `int` <: `long` <: `float` <: `double`
- Memory considerations affect primitive type selection

## Functions and Methods

### Computation Abstraction
- Functions group instructions under a name
- Allow composition at higher levels of abstraction
- Java functions (methods) require return type declaration

### Benefits of Functions
- Compartmentalization: Isolates computation and effects
- Implementation hiding: Separates what from how
- Code reuse: Reduces repetition through parameterization
- Abstraction barrier: Separates callers from implementers

### Function Types
- Pure functions: Same input always gives same output, no side effects
- Non-pure functions: May modify external state or depend on it
- Variable arguments: Methods accepting variable number of parameters
