> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Random

#java #programming

created: 1740600000000
updated: 1740595879005

---

<!--#region styles-->

<!--#endregion-->

# Java Random Class

## Overview

The `Random` class in Java provides methods for generating pseudo-random numbers of various types. It's part of the `java.util` package and is used when you need to introduce randomness into your applications.

## Basic Usage

```java
// Import the Random class
import java.util.Random;

// Create a Random object
Random random = new Random();

// Use the random object to generate random values
```

## Common Methods

### .nextInt()

```java
// Generate a random integer (can be positive or negative)
int randomNumber = random.nextInt();

// Generate a random integer from 0 (inclusive) to bound (exclusive)
int randomInRange = random.nextInt(10); // 0-9
```

### .nextInt() with Range

To generate a random integer within a specific range (min to max):

```java
// Generate random number between min (inclusive) and max (inclusive)
int min = 5;
int max = 10;
int randomInRange = random.nextInt(max - min + 1) + min; // 5-10
```

### .nextDouble()

```java
// Generate a random double between 0.0 (inclusive) and 1.0 (exclusive)
double randomDouble = random.nextDouble();

// Generate a random double within a specific range
double min = 5.0;
double max = 10.0;
double randomDoubleInRange = min + (max - min) * random.nextDouble();
```

### .nextBoolean()

```java
// Generate a random boolean (true or false)
boolean randomBoolean = random.nextBoolean();
```

### .nextLong()

```java
// Generate a random long value (can be positive or negative)
long randomLong = random.nextLong();
```

### .nextFloat()

```java
// Generate a random float value between 0.0 (inclusive) and 1.0 (exclusive)
float randomFloat = random.nextFloat();
```

## Seeding the Random Number Generator

You can initialize a Random object with a specific seed value to produce a repeatable sequence of random numbers, which is useful for testing:

```java
// Create a Random object with a specific seed
long seed = 123456;
Random random = new Random(seed);

// This will generate the same sequence of numbers every time
// when using the same seed
```

## Common Use Cases

### Random Element from Array

```java
String[] options = {"Apple", "Banana", "Cherry", "Date"};
String randomFruit = options[random.nextInt(options.length)];
```

### Simulating Dice Roll

```java
// Simulate rolling a six-sided die (1-6)
int dieRoll = random.nextInt(6) + 1;
```

### Generating Random Strings

```java
public static String generateRandomString(int length) {
    String characters = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
    StringBuilder result = new StringBuilder(length);
    Random random = new Random();

    for (int i = 0; i < length; i++) {
        result.append(characters.charAt(random.nextInt(characters.length())));
    }

    return result.toString();
}

// Generate a random string of length 10
String randomString = generateRandomString(10);
```

## Best Practices

> For cryptographic purposes, use `SecureRandom` instead of `Random`

> When seeding is not needed for security, create one Random instance and reuse it

> For simple random operations, consider using `Math.random()` which returns a double between 0.0 and 1.0

## Related Links

- [[java/math]]
- [[java/security/secure-random]]

> **Last reviewed**: November 28, 2025
