This repository contains a set of compact Java programs designed to illustrate core language features with clear, observable output. Each example is self-contained (usually a single file) and includes instructions on how to compile and run it from the command line.

Contents
Exception Demo
Interfaces and Final Modifier Demo
Command Line Arguments & String Class Demo
Packages Demo (Using and Importing Packages)
Exception Handling with Built-in and User-defined Exceptions
Multithreading Basics (Thread Creation, Synchronization)
Simple Multithreading with Output
Each section includes a brief description, how to compile, how to run, and expected output.

1) Exception Demo
What it demonstrates:

A built-in exception: ArrayIndexOutOfBoundsException
A user-defined exception: InvalidAgeException
Throwing, catching, and finally blocks
File: ExceptionDemo.java

How to run:

Compile: javac ExceptionDemo.java
Run: java ExceptionDemo
Expected output (sample):

ini
=== Demonstrating built-in exception: ArrayIndexOutOfBoundsException ===
Caught built-in exception: java.lang.ArrayIndexOutOfBoundsException: 5
Finished built-in exception demonstration.

=== Demonstrating user-defined exception: InvalidAgeException ===
Age 25 is valid.
Caught user-defined exception: Invalid age: -5. Age must be between 0 and 150.
Finished user-defined exception demonstration.
Notes:

The user-defined exception is defined as a static nested class for simplicity in a single file.
2) Interfaces and Final Modifier Demo
What it demonstrates:

Interfaces to define behavior
A final class that cannot be subclassed
A final method inside a class
Basic usage of static nested classes for a single-file demo
File: InterfaceFinalDemo.java

How to run:

Compile: javac InterfaceFinalDemo.java
Run: java InterfaceFinalDemo
Expected output (sample):

ini
Car: started, speed=10
Car: stopped, speed=0
Brand: Swift Motors
Notes:

The code shows interfaces Movable and Speakable, a final class Car, a final method honK, and a simple constant-based “brand” demonstration.
3) Command Line Arguments & String Class Demo
What it demonstrates:

Reading command line arguments
Basic String operations: interning, equality, substring, length, charAt, toUpperCase
String formatting with printf
StringBuilder usage for mutable strings
File: Demo.java

How to run:

Compile: javac Demo.java
Run with arguments: java Demo arg1 arg2
Expected output (sample):

ini
=== Command Line Arguments ===
arg[0] = arg1
arg[1] = arg2

=== String Class Demonstrations ===
s1: Hello
s2: Hello
s3: Hello
s1 == s2: true
s1 == s3: false
s1.equals(s3): true
Concatenated: Hello World
length of s1: 5
char at 1 in s1: e
substring(0,5) of s1: Hello
indexOf 'l' in s1: 2
toUpperCase: HELLO
Formatted: a=5, b=7, a+b=12
StringBuilder content: Mutable String Builder
Notes:

Demonstrates reference equality vs content equality for strings.
Uses StringBuilder to show efficient mutation.
4) Create and Use a Package
What it demonstrates:

Creating a package and a class inside it
Importing and using the packaged class from another file
Files:

src/com/example/utility/Greeter.java
java
package com.example.utility;

public class Greeter {
    private final String name;

    public Greeter(String name) {
        this.name = name;
    }

    public String greet() {
        return "Hello, " + name + "!";
    }
}
src/MainApp.java
java
import com.example.utility.Greeter;

public class MainApp {
    public static void main(String[] args) {
        Greeter greeter = new Greeter("Alice");
        System.out.println(greeter.greet());
    }
}
How to compile and run (example with a simple output directory layout):

Compile:
javac -d out src/com/example/utility/Greeter.java
javac -d out -cp out src/MainApp.java
Run:
java -cp out MainApp
Expected output:

Hello, Alice!
Notes:

If you use a build tool like Maven or Gradle, the package layout can be reflected in src/main/java/com/example/utility/Greeter.java, and you can configure the project accordingly.
5) Thread Demo (Multithreading Concepts)
What it demonstrates:

Creating threads by extending Thread and by implementing Runnable
Starting and joining threads
A shared, synchronized counter to illustrate safe concurrent access
File: ThreadDemo.java

How to run:

Compile: javac ThreadDemo.java
Run: java ThreadDemo
Expected output (sample, order may vary due to scheduling):

arduino
Main thread started.
Thread-Up incremented counter: 0 -> 1
Thread 2 incremented counter: 1 -> 2
Main thread finished. Final counter = 15
Notes:

The example uses a synchronized method to protect a shared static counter.
For more advanced scenarios, consider ExecutorService and thread pools.
6) Simple Thread Demo
What it demonstrates:

A minimalist thread example with two threads printing interleaved messages
The main thread also prints to show interleaving
File: ThreadSimpleDemo.java

How to run:

Compile: javac ThreadSimpleDemo.java
Run: java ThreadSimpleDemo
Expected output (sample, interleaving may vary):

arduino
Thread 1 - count 1
Thread 2 - count 1
Main thread - count 1
Thread 1 - count 2
Thread 2 - count 2
Main thread - count 2
...
Done.
Notes:

This is the simplest form of a multithreading example to illustrate basic thread creation and scheduling.
How to Compile All Examples (Optional)
If you want to compile all single-file demos together from a directory, you can use a simple shell script or a Makefile. Here’s a basic approach:

Create a build script (build.sh or Makefile) that:
Compiles each Java file with javac
Runs each program to verify output
Example (bash script):

bash
#!/bin/bash
set -e

# Compile
javac ExceptionDemo.java
javac InterfaceFinalDemo.java
javac Demo.java
javac ThreadDemo.java
javac ThreadSimpleDemo.java

# Run (adjust package/class names as needed)
java ExceptionDemo
java InterfaceFinalDemo
java Demo a b
java ThreadDemo
java ThreadSimpleDemo
Tips and Best Practices
When experimenting with concurrency, prefer ExecutorService and higher-level concurrency utilities from java.util.concurrent for better scalability and manageability.
Use meaningful class and method names to reflect the demonstrated concept.
If you extend examples, keep them self-contained and clearly comment what concept is being illustrated.
For larger projects, consider using a build tool (Maven or Gradle) and a conventional multi-module structure.
