> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Do_while

#javascript #programming #javascript #core-concepts

created: 1738170968099
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## do-while Loop

The `do-while` loop is similar to the `while` loop, but the code block is executed at least once, even if the condition is `false`. The syntax of the `do-while` loop is as follows:

```javascript
do {
  // code to be executed
} while (condition);
```

Here is an example of a `do-while` loop:

```javascript
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

In this example, the loop will run five times, and the output will be the same as the `for` and `while` loop examples. The `do-while` loop is useful when you want to execute the code block at least once before checking the condition.

> **Last reviewed**: November 28, 2025
