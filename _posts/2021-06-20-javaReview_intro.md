---
title: "[Java] #1 Java11: Intro"
excerpt: "Java and its features"

categories:
  - Java
tags:
  - [Java]

toc: true

date: 2021-06-20
last_modified_at: 2021-07-02
---

This is a self note while taking the online course from:
**LinkedIn Learning: Java 11+ Essential Training** by _David Gassner_

---

## 1. Principle of Java

- Simple, object-oriented, and familiar
- Robust and secure --> designing everything as _object_
- Architecture neutral and portable

  - compiles to _byte code_ (not machine code) --> can be loaded on any operating system that has a Java virtual machine
  - applications are portable between platforms **without recompiling**

    Java runtime architecture:
    ![java runtime architecture](/assets/images/java_architecture.png)

- High performance
- Interpreted, threaded, and dynamic
  - compiled to a format that's interpreted at run time (directly machine code X) ==> **interpreted**
  - easy to build application do more than one thing at the same time ==> **threaded(multi-threads)**

## 2. Java syntax

- Java Class file

  - all code is defined in classes
  - java source code (_.java_ file) can be compiled using _javac_ command
  - _java_ command runs the compiled bytecode file with JVM

  ```java
  pacakge com.example; // 1)

  public class Main { // 2)
      public static void main(String[] args) {
          System.out.println("Hello World");
      }
  }
  ```

  - 1. package declaration: indicates where the file is stored in terms of the directory structure of the application (organizing the code)
  - 2. class declaration: class name + class members + main method

- Identifier Conventions

  - Classes start with an uppercase character
  - Method, variables start with an lowercase character
  - Constants are all uppercase

  ## 3. Memory Management in Java

  - Java **automatically** allocates and deallocates memory as needed (in runtime)
  - Local variables, function calls --> **Stack**
  - Objects, member variables --> **Heap**
  - Objects are reatained in memory **until dereferenced**
  - After dereferenced --> _Garbage Collector_

  ### Tips for memory management:

  - minimize the number of objects
  - use _System methods_ to check memory usage (_Runtime.maxMemory()_, _Runtime.totalMemory()_, ...)
