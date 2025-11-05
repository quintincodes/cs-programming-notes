# Java Data Types Deep Dive

#java #programming #java #core-concepts #data-types

created: 1723292400000
updated: 1732750000000

---

> Last reviewed: 2025-11-28

## Overview

Java is a strongly typed language, which means every variable must have a declared type. Understanding data types is fundamental to Java programming.

## Primitive Data Types

Java has 8 primitive data types:

### Integer Types

#### byte

- Size: 8 bits (1 byte)
- Range: -128 to 127
- Default value: 0
- Use case: Save memory in large arrays

```java
byte age = 25;
byte temperature = -10;
```

#### short

- Size: 16 bits (2 bytes)
- Range: -32,768 to 32,767
- Default value: 0
- Use case: Save memory when you know the value range

```java
short year = 2025;
short population = 15000;
```

#### int

- Size: 32 bits (4 bytes)
- Range: -2,147,483,648 to 2,147,483,647
- Default value: 0
- Use case: Most commonly used integer type

```java
int studentCount = 1500;
int salary = 75000;
```

#### long

- Size: 64 bits (8 bytes)
- Range: -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
- Default value: 0L
- Use case: Large numbers, timestamps

```java
long worldPopulation = 7800000000L;
long timestamp = System.currentTimeMillis();
```

### Floating-Point Types

#### float

- Size: 32 bits (4 bytes)
- Precision: ~6-7 decimal digits
- Default value: 0.0f
- Use case: When precision is not critical

```java
float price = 19.99f;
float percentage = 0.15f;
```

#### double

- Size: 64 bits (8 bytes)
- Precision: ~15-17 decimal digits
- Default value: 0.0d
- Use case: Default choice for decimal numbers

```java
double pi = 3.141592653589793;
double distance = 384400.0; // km to moon
```

### Boolean Type

#### boolean

- Size: 1 bit (implementation dependent)
- Values: true, false
- Default value: false
- Use case: Conditional logic

```java
boolean isStudent = true;
boolean hasPermission = false;
boolean isValid = (age >= 18);
```

### Character Type

#### char

- Size: 16 bits (2 bytes)
- Range: 0 to 65,535 (Unicode characters)
- Default value: '\u0000'
- Use case: Single characters

```java
char grade = 'A';
char symbol = '@';
char unicode = '\u0041'; // 'A'
```

## Reference Data Types

Reference types store the memory address of the object, not the object itself.

### String

```java
String name = "John Doe";
String message = "Hello, World!";
String empty = ""; // empty string
String nullString = null; // null reference
```

### Arrays

```java
int[] numbers = {1, 2, 3, 4, 5};
String[] names = new String[3];
double[][] matrix = new double[3][3];
```

### Objects

```java
Scanner scanner = new Scanner(System.in);
ArrayList<String> list = new ArrayList<>();
Date today = new Date();
```

## Type Conversion

### Implicit Conversion (Widening)

```java
int num = 100;
long bigNum = num;     // int to long
double decimal = num;   // int to double
```

### Explicit Conversion (Narrowing)

```java
double pi = 3.14159;
int wholePart = (int) pi;  // 3 (loses decimal part)

long bigNumber = 1000L;
int smallNumber = (int) bigNumber;
```

## Best Practices

1. **Choose appropriate size**: Use `int` for most integer operations
2. **Use `double` for floating-point**: Preferred over `float`
3. **Initialize variables**: Avoid using uninitialized variables
4. **Meaningful names**: Use descriptive variable names
5. **Constants**: Use `final` for values that don't change

```java
final int MAX_STUDENTS = 30;
final double PI = 3.141592653589793;
final String COMPANY_NAME = "Tech Corp";
```

## Common Mistakes

1. **Integer overflow**: Numbers exceeding range wrap around
2. **Floating-point precision**: Avoid exact equality comparisons
3. **Null pointer exceptions**: Check for null before using references
4. **Character vs String**: Single quotes for char, double quotes for String

```java
// Wrong
if (0.1 + 0.2 == 0.3) { /* This may be false! */ }

// Right
if (Math.abs((0.1 + 0.2) - 0.3) < 0.0001) { /* Better approach */ }
```
