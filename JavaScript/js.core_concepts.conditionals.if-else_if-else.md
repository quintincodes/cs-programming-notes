> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: If Else_if Else

#javascript #programming #javascript #core-concepts

created: 1738163286280
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## The `if...else if...else` Statement

The `if...else if...else` statement executes different blocks of code for different conditions.

```javascript
if (condition1) {
  // code to be executed if condition1 is true
} else if (condition2) {
  // code to be executed if condition2 is true
} else {
  // code to be executed if none of the conditions are true
}
```

Here is an example of an `if...else if...else` statement:

```javascript
let x = 10;

if (x > 20) {
  console.log("x is greater than 20");
} else if (x < 20) {
  console.log("x is less than 20");
} else {
  console.log("x is equal to 20");
}
```

In this example, the condition `x > 20` is false, and the condition `x < 20` is true, so the output will be:

```
x is less than 20
```

> **Last reviewed**: November 28, 2025
