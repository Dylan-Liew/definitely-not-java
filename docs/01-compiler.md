# Program and Compiler

## Software Programs
- A program is a collection of data variables and instructions
- Programs are written in programming languages using keywords, symbols, and names
- Programming languages provide higher level abstraction for complex instructions
- Programming languages are used to communicate instructions to a computer.

## Compiler and Interpreter Execution Process
- Java compiler (`javac`) compiles source code (.java) into bytecode (.class)
- Compilation:
  ```
  javac Hello.java    # compile Hello.java
  ```
- JVM (`java`) executes the bytecode by translating it into machine code
- Execution:
  ```
   java Hello         # runs the program
  ```
> Notes: [Launch Single-File Source-Code Programs](https://openjdk.org/jeps/330) allows running Java files without explicit compilation. E.g. `java Hello.java`

## Java Shell (`jshell`)
-  `jshell` is a REPL (Read–Eval–Print Loop) for Java introduced in Java 9. 
- Start it by running:
  ```bash
  jshell
  ```
- Modes:
    - Interactive mode for experimentation.
    - Script mode using `.jsh` files.
- Usage notes:
    - Useful for quick testing, learning, and prototyping without creating full source files.
    - You can declare variables, define methods, and call APIs directly in the REPL.

## Compiler Functions
- Translates source code to machine code/bytecode
- Checks code for syntax errors
    - Compilation errors are caught during development, allowing programmers to fix them early.
    - Runtime errors are less desirable because they occur while the program is running, potentially affecting users.
    - The goal is to catch as many errors as possible at compile time, rather than during execution.
- Performs type checking
- Can be either:
    - Conservative: Reports error if possibility of incorrect statement
    - Permissive: Only reports error if statement is definitely incorrect

## Compiler Limitations
- Cannot detect all runtime errors during compilation
- Cannot always determine if code will be executed
- Cannot always determine variable values at compile time

## Workflow
1. Create or edit file containing Java program (`Hello.java`) with an editor (`vim`).
2. Compile source code using a compiler (`javac Hello.java`) to produce a bytecode file (`.class`)
3. Execute the program (`java Hello`)