> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Switch_statements

#javascript #programming #javascript #core-concepts

created: 1738167414155
updated: 1738275940378

---

<!--#region styles-->

<!--#endregion-->

## The `switch` Statement

The `switch` statement is used to perform different actions based on different conditions.

```javascript
switch (expression) {
  case value1:
    // code to be executed if expression is equal to value1
    break;
  case value2:
    // code to be executed if expression is equal to value2
    break;
  default:
  // code to be executed if expression is different from all values
}
```

Here is an example of a `switch` statement:

```javascript
let day = "Monday";

switch (day) {
  case "Monday":
    console.log("Today is Monday");
    break;
  case "Tuesday":
    console.log("Today is Tuesday");
    break;
  default:
    console.log("Today is not Monday or Tuesday");
}
```

In this example, the value of `day` is `'Monday'`, so the output will be:

```
Today is Monday
```

> **Last reviewed**: November 28, 2025
