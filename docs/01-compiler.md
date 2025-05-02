# Java Program and Compiler

## Software Programs
- A program is a collection of data variables and instructions
- Programs are written in programming languages using keywords, symbols, and names
- Programming languages provide higher level abstraction for complex instructions

## Program Execution Methods
- Two main approaches to execute programs:
    1. Compilation: Translates entire program to machine code before execution
    2. Interpretation: Reads and executes program statements one at a time

## Java Execution
- Java uses a hybrid approach: "Write once, run anywhere" principle
- Two ways to run Java programs:
    1. Compile to bytecode first, then interpret/compile via JVM
    2. Direct interpretation using Java interpreter
- Java Virtual Machine (JVM):
    - Platform-specific runtime environment
    - Converts bytecode to machine code using Just-In-Time (JIT) compilation
    - Handles memory management and garbage collection
    - Provides platform independence through abstraction layer

## Compilation Process
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
- Common mistakes to avoid:
    - Confusing `javac` and `java`
    - [Launch Single-File Source-Code Programs](https://openjdk.org/jeps/330) before compiling. E.g. `java Hello.java`
- Classpath considerations:
    - Default is current directory
    - Set with `-cp` or `-classpath` option
    - Controls where Java looks for classes

## Java Shell (jshell)
- Interactive tool for Java code evaluation (introduced in Java 9)
- Allows direct code testing without compilation (REPL environment)
- Useful for learning and experimentation
- Can run in two modes:
      - Interactive mode: `jshell` at command prompt
      - Script mode with .jsh files: `jshell filename.jsh`
- Basic jshell commands:
      - `/list`: Show entered code snippets
      - `/exit`: Exit the shell
      - `/help`: Display help information
      - `/imports`: List imported packages

## Compiler Functions
- Translates source code to machine code/bytecode
- Checks code for syntax errors
- Performs type checking
- Can be either:
    - Conservative: Reports error if possibility of incorrect statement
    - Permissive: Only reports error if statement is definitely incorrect

## Compiler Limitations
- Cannot detect all runtime errors during compilation
- Cannot always determine if code will be executed
- Cannot always determine variable values at compile time
