# Program and Compiler

## Software Programs
- A program is a collection of data variables and instructions
- Programs are written in programming languages using keywords, symbols, and names
- Programming languages provide higher level abstraction for complex instructions

## Program Execution Methods
- Two main approaches to execute programs:
    1. Compilation: Translates entire program to machine code before execution
    2. Interpretation: Reads and executes program statements one at a time

## Java Execution
- Two ways to run Java programs:
    1. Compile to bytecode first, then interpret/compile via JVM
    2. Direct interpretation using Java interpreter

## Compilation Process
- Java compiler (`javac`) compiles source code (.java) to bytecode (.class)
- Basic compilation steps:
  ```
  javac Hello.java    # creates Hello.class
  java Hello          # runs the program
  ```
- Common mistakes to avoid:
    - Confusing `javac` and `java`
    - [Launch Single-File Source-Code Programs](https://openjdk.org/jeps/330) before compiling. E.g. `java Hello.java`

## Java Shell (jshell)
- Interactive tool for Java code evaluation
- Allows direct code testing without compilation
- Useful for learning and experimentation
- Can run in two modes:
      - Interactive mode
      - Script mode with .jsh files

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
