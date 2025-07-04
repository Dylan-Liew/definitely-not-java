# Program and Compiler

## Software Programs
- A program is a collection of data variables and instructions
- Programs are written in programming languages using keywords, symbols, and names
- Programming languages provide higher level abstraction for complex instructions
- Programming languages are used to dictate these instructions to the computer.

## Program Execution Methods
- Two main approaches to execute programs:
    1. Compilation: Translates entire program to machine code before execution
    2. Interpretation: Reads and executes program statements one at a time

## Java Execution
- Two ways to run Java programs:
    1. Complier and Interpreter
        - A software tool reads the program written in Java and translates it into bytecode first.
        - Then during execution, the bytecode is interpreted and complied by Java Virtual Machine(JVM) into machine code
    2. Interpreter 
        - Direct interpretation using Java interpreter

## Compilation Process
- Java compiler (`javac`) compiles source code (.java) to JVM language AKA bytecode (.class)
- Basic compilation steps:
  ```
  javac Hello.java    # creates Hello.class
 
  ```
- Invoke JVM (`java`) and execute the bytecode by interpreting JVM language(bytecode) to Machine language(x86-64).
- Basic Execution step:
  ```
   java Hello          # runs the program
  
  ```
- Common mistakes to avoid:
    - Confusing `javac` and `java`
    - [Launch Single-File Source-Code Programs](https://openjdk.org/jeps/330) before compiling. E.g. `java Hello.java`

## Java Shell (jshell)
- Interactive tool for Java code evaluation (read in Java statements, evaluate them, and print the results.)
- Allows direct code testing without compilation
- Useful for learning and experimentation
- Can run in two modes:
      - Interactive mode
      - Script mode with .jsh files

## Compiler Functions
- Translates source code to machine code/bytecode
- Checks code for syntax errors (grammar)
      - During compilation is still under the control of the programmer.
      - Runtime error is less desirable as it might occur when customers are running the code.
      - Try to detect errors as much as possible during compilation instead of Runtime
- Performs type checking
- Can be either:
    - Conservative: Reports error if possibility of incorrect statement
    - Permissive: Only reports error if statement is definitely incorrect

## Compiler Limitations
- Cannot detect all runtime errors during compilation
- Cannot always determine if code will be executed
- Cannot always determine variable values at compile time

## Workflow
1. Create or edit file containing java program (Hello.java) with an editior (vim). This will be the source code
2. Compile source code using a compiler (javac Hello.java) to produce a bytecode file (.class)
3. Execute the program and test
    - If find incorrect result, restart from the frist step again until the program is desirable.