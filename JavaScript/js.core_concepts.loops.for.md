> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: For

#javascript #programming #javascript #core-concepts

created: 1738105763926
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## for Loop

The `for` loop is used to execute a block of code a specified number of times. The syntax of the `for` loop is as follows:

```javascript
for (initialization; condition; increment / decrement) {
  // code to be executed
}
```

The `initialization` statement is executed only once at the beginning of the loop. The `condition` is evaluated before each iteration. If the condition is `true`, the code block is executed. The `increment / decrement` statement is executed after each iteration. The loop continues until the condition is `false`.

Here is an example of a `for` loop:

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

In this example, the loop will run five times, and the output will be:

```
0
1
2
3
4
```

> **Last reviewed**: November 28, 2025
