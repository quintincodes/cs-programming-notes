> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Scanner

#java #programming

created: 1740600000000
updated: 1740600000000

---

<!--#region styles-->

<!--#endregion-->

# Java Scanner Class

## Overview

The Scanner class in Java is used to read input data from various sources like input streams, files, or strings. It is part of the `java.util` package.

## Basic Usage

```java
// Import the Scanner class
import java.util.Scanner;

// Create a Scanner object for reading from standard input
Scanner scanner = new Scanner(System.in);

// Use scanner to read input
// ...

// Close the scanner when done
scanner.close();
```

## Common Methods

### .nextLine()

```java
String fullLine = scanner.nextLine();
```

- Reads a complete line of input (including spaces)
- Returns the input as a String
- Advances the scanner past the current line

### .next()

```java
String nextWord = scanner.next();
```

- Reads the next token (word) up to a whitespace
- Returns the token as a String
- Useful for reading single words

### .nextInt()

```java
int number = scanner.nextInt();
```

- Reads the next token as an integer
- Throws InputMismatchException if the next token is not a valid integer
- **Note:** Leaves the newline character in the input buffer

### .nextBoolean()

```java
boolean flag = scanner.nextBoolean();
```

- Reads the next token as a boolean value
- Returns true for "true" and false for "false" (case-insensitive)
- Throws InputMismatchException if the next token is not a valid boolean

## Common Issues and Solutions

### The Newline Character Problem

When mixing `nextInt()` or other primitive reading methods with `nextLine()`, you may encounter an issue where `nextLine()` reads the leftover newline character:

```java
// Problematic code
int age = scanner.nextInt();
System.out.print("Enter your name: ");
String name = scanner.nextLine(); // This will immediately return an empty string!
```

Solution:

```java
int age = scanner.nextInt();
scanner.nextLine(); // Consume the leftover newline
System.out.print("Enter your name: ");
String name = scanner.nextLine(); // Now this works correctly
```

## Best Practices

> Always close the Scanner when done to prevent resource leaks

> Import the Scanner class explicitly with `import java.util.Scanner;`

> Use `scanner.hasNext()` or similar methods to check if more input is available

> When reading mixed types of data, be aware of the newline character issue

## Example: Complete Input Program

```java
import java.util.Scanner;

public class UserInputExample {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = scanner.nextLine();

        System.out.print("Enter your age: ");
        int age = scanner.nextInt();
        scanner.nextLine(); // Consume newline

        System.out.print("Enter your city: ");
        String city = scanner.nextLine();

        System.out.print("Are you a student? (true/false): ");
        boolean isStudent = scanner.nextBoolean();

        System.out.println("\nUser Information:");
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("City: " + city);
        System.out.println("Student: " + isStudent);

        scanner.close();
    }
}
```

## Related Links

- [[java/io/printf]]
- [[java/core_concepts/data_types/primitive]]
- [[java/exceptions]]

> **Last reviewed**: November 28, 2025
