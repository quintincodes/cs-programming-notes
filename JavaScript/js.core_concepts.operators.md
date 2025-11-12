> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Operators

#javascript #programming #javascript #core-concepts

created: 1734086003639
updated: 1734089921312

---

# Operators in JavaScript

Operators are used to perform operations on variables and values. JavaScript has the following types of operators:

- Assignment operators

- Comparison operators
- Arithmetic operators
- Bitwise operators
- Logical operators
- String operators
- Conditional (ternary) operator
- Comma operator
- Unary operators
- Relational operators
- Grouping operators
- Precedence operators
- Destructuring operators
- Spread operators

## Assignment Operators

Assignment operators are used to assign values to variables. In JavaScript, we have the following assignment operators:

- `=` : assigns a value to a variable

- `+=` : adds a value to a variable
- `-=` : subtracts a value from a variable
- `*=` : multiplies a variable by a value
- `/=` : divides a variable by a value
- `%=` : assigns a remainder to a variable
- `**=` : raises a variable to the power of a value
- `<<=` : shifts a variable to the left
- `>>=` : shifts a variable to the right
- `>>>=` : shifts a variable to the right and fills with zeros

### Assignment Operators Examples

```js
let x = 10;

// Basic assignment
x = 20; // x = 20

// Compound assignments
x += 5; // x = 25 (equivalent to x = x + 5)
x -= 3; // x = 22 (equivalent to x = x - 3)
x *= 2; // x = 44 (equivalent to x = x * 2)
x /= 4; // x = 11 (equivalent to x = x / 4)
x %= 3; // x = 2 (equivalent to x = x % 3)
x **= 3; // x = 8 (equivalent to x = x ** 3)
```

## Arithmetic Operators

Arithmetic operators perform mathematical operations on numbers.

- `+` : Addition
- `-` : Subtraction
- `*` : Multiplication
- `/` : Division
- `%` : Modulus (remainder)
- `**` : Exponentiation
- `++` : Increment
- `--` : Decrement

### Arithmetic Operators Examples

```js
let a = 10,
  b = 3;

console.log(a + b); // 13 (Addition)
console.log(a - b); // 7 (Subtraction)
console.log(a * b); // 30 (Multiplication)
console.log(a / b); // 3.333... (Division)
console.log(a % b); // 1 (Modulus)
console.log(a ** b); // 1000 (Exponentiation)

// Increment/Decrement
let count = 5;
console.log(++count); // 6 (Pre-increment)
console.log(count++); // 6 (Post-increment, count becomes 7)
console.log(--count); // 6 (Pre-decrement)
console.log(count--); // 6 (Post-decrement, count becomes 5)
```

## Comparison Operators

Comparison operators compare two values and return a boolean result.

- `==` : Equal to (loose equality)
- `===` : Strict equal to
- `!=` : Not equal to (loose inequality)
- `!==` : Strict not equal to
- `>` : Greater than
- `<` : Less than
- `>=` : Greater than or equal to
- `<=` : Less than or equal to

### Comparison Operators Examples

```js
let x = 5,
  y = "5";

console.log(x == y); // true (loose equality, type coercion)
console.log(x === y); // false (strict equality, different types)
console.log(x != y); // false (loose inequality)
console.log(x !== y); // true (strict inequality, different types)

console.log(x > 3); // true
console.log(x < 10); // true
console.log(x >= 5); // true
console.log(x <= 4); // false
```

> **Last reviewed**: November 28, 2025
