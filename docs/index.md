# Definitely Not Java

Java is a high-level, class-based, object-oriented programming language and platform designed for portability: Java source is compiled to bytecode that runs on the Java Virtual Machine (JVM), allowing the same program to run on different operating systems that have a compatible JVM. 

The language was originally created at Sun Microsystems and is now implemented and distributed through projects and vendors such as OpenJDK, Oracle, and Eclipse Adoptium.

## Java installation

- [Official OpenJDK](https://openjdk.org/)
- [Oracle JDK downloads](https://www.oracle.com/java/technologies/downloads/)
- [Eclipse Adoptium (Temurin builds)](https://adoptium.net/)

Choose a distribution and the correct installer for your platform (Windows/macOS/Linux). 

## Java compiler `javac`

- `javac` translates Java source files (`.java`) into Java bytecode class files (`.class`) that the JVM can execute.
- Typical usage:
```bash
javac Hello.java    # produces Hello.class
java Hello          # runs the compiled bytecode on the JVM
```

---

<small>This repository is inspired by CS2030S (School of Computing, National University of Singapore).</small>