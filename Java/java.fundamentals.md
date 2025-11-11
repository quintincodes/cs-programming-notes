---
title: Java Fundamentals
#tags: #java #programming #fundamentals #core-concepts
created: 1739571858911
updated: 1732750000000
---

> Last reviewed: 2025-11-28

<!--#region styles-->
<!--#endregion-->

# Java Fundamentals

## Overview

Java is a powerful, object-oriented programming language that follows the "write once, run anywhere" philosophy. This guide covers essential Java concepts for beginners and intermediate developers.

## Core Concepts

### String Concatenation

String concatenation is the operation of joining two or more strings together. In Java, this is performed using the `+` operator between string variables or literals.

```java
String firstName = "John";
String lastName = "Doe";
String fullName = firstName + " " + lastName; // "John Doe"
```

## Syntax Examples

### Scanner Object

```java
// Import the Scanner class from java.util package
import java.util.Scanner;

// Create a Scanner object
Scanner scanner = new Scanner(System.in);

// Get user input
String name = scanner.nextLine();
int age = scanner.nextInt();
boolean isStudent = scanner.nextBoolean();

// Handle mixed input types (common issue)
scanner.nextLine(); // Consume leftover newline

// Always close the scanner when done
scanner.close();
```

### Improved Input Handling

```java
// Better practice: Use try-with-resources
try (Scanner scanner = new Scanner(System.in)) {
    System.out.print("Enter your name: ");
    String name = scanner.nextLine();

    System.out.print("Enter your age: ");
    int age = scanner.nextInt();

    System.out.println("Hello " + name + ", you are " + age + " years old.");
}
```

### Random Object

```java
// Import the Random class
import java.util.Random;

// Create a Random object
Random random = new Random();

// Generate random values
int randomInt = random.nextInt(100); // 0-99
double randomDouble = random.nextDouble(); // 0.0-1.0
```

## Topic References

### Data Types

- [[java/core_concepts/data_types/primitive]]
- [[java/core_concepts/data_types/reference]]

### Input/Output

- [[java/io/scanner]] - Scanner object and methods
- [[java/io/printf]] - Output formatting
- [[java/string/format-specifiers]] - Format specifiers: %[flags][width][.precision][format-specifiers]

### Operators

- [[java/core_concepts/operators/assignment]] - Assignment operators
- [[java/core_concepts/operators/augmented-assignment]] - Augmented assignment operators
- [[java/core_concepts/operators/increment-decrement]] - Increment and decrement operators
- [[java/core_concepts/operators/precedence]] - PEMDAS and operator precedence

### Control Flow

- [[java/core_concepts/conditionals/if-statements]] - If statements

### Utility Classes

- [[java/util/random]] - Random number generation
- [[java/math]] - Math methods (.pow(), .abs(), .sqrt(), etc.)
- [[java/string/methods]] - String methods including .isEmpty()

## Key Points

> To use the scanner object, it must be imported using the util package: `import java.util.Scanner`

> It's good practice to close the scanner after using it with `scanner.close()`

> When accepting strings after integers with Scanner, the newline character can cause issues. Fix by adding an extra `scanner.nextLine()` after reading integers.

> PI and E are static properties (fields) of the Math class: `Math.PI` and `Math.E`

> In Java classes, members consist of methods and fields (both represent the class's functionality and state)

> TIP: To use superscript in VSCode, use Numlock + Alt + 0178 for ² or Alt + 0179 for ³

> Format specifiers in printf/String.format use % as placeholders before the variables they represent

## Related Resources

- [Oracle Java Documentation](https://docs.oracle.com/en/java/javase/17/docs/api/index.html)
- [Java Scanner Class Documentation](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Scanner.html)
- [Java Math Class Documentation](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Math.html)
