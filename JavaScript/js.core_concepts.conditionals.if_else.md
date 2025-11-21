> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: If_else

#javascript #programming #javascript #core-concepts

created: 1738106001211
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## The `if...else` Statement

The `if...else` statement executes a block of code if a specified condition is true and another block of code if the condition is false.

![[js/syntax/conditionals#ifelse-statement-syntax]]

Here is an example of an `if...else` statement:

```javascript
let x = 10;

if (x > 20) {
  console.log("x is greater than 20");
} else {
  console.log("x is less than or equal to 20");
}
```

In this example, the condition `x > 20` is false, so the output will be:

```
x is less than or equal to 20
```

## The Ternary Operator

The ternary operator is a shorthand way of writing an `if...else` statement.

```javascript
condition ? expression1 : expression2;
```

Here is an example of the ternary operator:

```javascript
let x = 10;

let result = x > 5 ? "x is greater than 5" : "x is less than or equal to 5";

console.log(result);
```

In this example, the condition `x > 5` is true, so the output will be:

```
x is greater than 5
```

The ternary operator can be used to assign values to variables based on conditions.

> **Last reviewed**: November 28, 2025
