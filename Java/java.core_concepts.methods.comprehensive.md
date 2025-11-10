# Java Methods and Functions

#java #programming #methods #functions #core-concepts

created: 1723292400000
updated: 1732750000000

---

> Last reviewed: 2025-11-28

## Overview

Methods in Java are blocks of code that perform specific tasks. They enable code reusability, modularity, and better organization.

## Method Syntax

```java
[access_modifier] [static] [return_type] methodName([parameters]) {
    // method body
    [return statement;]
}
```

## Access Modifiers

- **public**: Accessible from anywhere
- **private**: Accessible only within the same class
- **protected**: Accessible within package and subclasses
- **default** (no modifier): Accessible within the same package

## Basic Method Examples

### Void Methods (No Return Value)

```java
public void greetUser(String name) {
    System.out.println("Hello, " + name + "!");
}

public void displayInfo() {
    System.out.println("This is a simple method");
}

// Calling void methods
greetUser("Alice");
displayInfo();
```

### Methods with Return Values

```java
public int addNumbers(int a, int b) {
    return a + b;
}

public double calculateArea(double radius) {
    return Math.PI * radius * radius;
}

public boolean isEven(int number) {
    return number % 2 == 0;
}

// Using returned values
int sum = addNumbers(5, 3);
double area = calculateArea(4.5);
boolean even = isEven(10);
```

## Static Methods

Static methods belong to the class rather than instances.

```java
public class MathUtils {
    public static int multiply(int a, int b) {
        return a * b;
    }

    public static double average(double[] numbers) {
        double sum = 0;
        for (double num : numbers) {
            sum += num;
        }
        return sum / numbers.length;
    }
}

// Calling static methods
int product = MathUtils.multiply(4, 5);
double avg = MathUtils.average(new double[]{1.5, 2.5, 3.5});
```

## Method Overloading

Multiple methods with the same name but different parameters.

```java
public class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public int add(int a, int b, int c) {
        return a + b + c;
    }

    public String add(String a, String b) {
        return a + b;
    }
}

// Usage
Calculator calc = new Calculator();
int intSum = calc.add(5, 3);
double doubleSum = calc.add(5.5, 3.2);
int tripleSum = calc.add(1, 2, 3);
String stringSum = calc.add("Hello", "World");
```

## Parameter Passing

### Pass by Value (Primitives)

```java
public void modifyPrimitive(int x) {
    x = x * 2;  // Only changes local copy
}

int number = 5;
modifyPrimitive(number);
System.out.println(number);  // Still 5
```

### Pass by Reference (Objects)

```java
public void modifyArray(int[] arr) {
    arr[0] = 100;  // Changes original array
}

int[] numbers = {1, 2, 3};
modifyArray(numbers);
System.out.println(numbers[0]);  // Now 100
```

## Variable Arguments (Varargs)

```java
public int sum(int... numbers) {
    int total = 0;
    for (int num : numbers) {
        total += num;
    }
    return total;
}

// Can be called with any number of arguments
int result1 = sum(1, 2, 3);
int result2 = sum(1, 2, 3, 4, 5);
int result3 = sum();  // Empty arguments
```

## Recursive Methods

Methods that call themselves.

```java
public int factorial(int n) {
    if (n <= 1) {
        return 1;  // Base case
    }
    return n * factorial(n - 1);  // Recursive call
}

public int fibonacci(int n) {
    if (n <= 1) {
        return n;
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Usage
int fact5 = factorial(5);  // 120
int fib6 = fibonacci(6);   // 8
```

## Constructor Methods

Special methods for object initialization.

```java
public class Student {
    private String name;
    private int age;

    // Default constructor
    public Student() {
        this.name = "Unknown";
        this.age = 0;
    }

    // Parameterized constructor
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Constructor overloading
    public Student(String name) {
        this.name = name;
        this.age = 18;  // Default age
    }
}

// Creating objects
Student student1 = new Student();
Student student2 = new Student("John", 20);
Student student3 = new Student("Alice");
```

## Getter and Setter Methods

```java
public class Person {
    private String name;
    private int age;

    // Getter methods
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    // Setter methods
    public void setName(String name) {
        if (name != null && !name.trim().isEmpty()) {
            this.name = name;
        }
    }

    public void setAge(int age) {
        if (age >= 0 && age <= 150) {
            this.age = age;
        }
    }
}
```

## Method Best Practices

1. **Single Responsibility**: Each method should do one thing well
2. **Descriptive Names**: Use clear, meaningful method names
3. **Keep it Short**: Methods should be concise and focused
4. **Minimize Parameters**: Too many parameters make methods hard to use
5. **Return Early**: Use early returns to reduce nesting

```java
// Good practice
public boolean isValidPassword(String password) {
    if (password == null) return false;
    if (password.length() < 8) return false;
    if (!password.matches(".*[A-Z].*")) return false;
    if (!password.matches(".*[0-9].*")) return false;
    return true;
}

// Avoid deep nesting
public String formatUserInfo(User user) {
    if (user == null) {
        return "No user data";
    }

    if (user.getName() == null) {
        return "User name not available";
    }

    return String.format("User: %s, Age: %d",
                        user.getName(), user.getAge());
}
```

## Common Method Patterns

### Validation Methods

```java
public boolean isValidEmail(String email) {
    return email != null &&
           email.contains("@") &&
           email.indexOf("@") > 0 &&
           email.lastIndexOf("@") == email.indexOf("@");
}
```

### Utility Methods

```java
public static String capitalize(String text) {
    if (text == null || text.isEmpty()) {
        return text;
    }
    return text.substring(0, 1).toUpperCase() +
           text.substring(1).toLowerCase();
}
```

### Builder Pattern Methods

```java
public class Pizza {
    private String size;
    private boolean cheese;
    private boolean pepperoni;

    public Pizza setSize(String size) {
        this.size = size;
        return this;
    }

    public Pizza addCheese() {
        this.cheese = true;
        return this;
    }

    public Pizza addPepperoni() {
        this.pepperoni = true;
        return this;
    }
}

// Method chaining
Pizza pizza = new Pizza()
    .setSize("Large")
    .addCheese()
    .addPepperoni();
```
