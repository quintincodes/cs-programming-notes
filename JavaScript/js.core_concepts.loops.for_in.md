> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: For_in

#javascript #programming #javascript #core-concepts

created: 1738170894403
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## for-in Loop

The `for-in` loop is used to iterate over the properties of an object. The syntax of the `for-in` loop is as follows:

```javascript
for (variable in object) {
  // code to be executed
}
```

Here is an example of a `for-in` loop:

```javascript
const person = { name: "John", age: 30, city: "New York" };
for (let key in person) {
  console.log(key + ": " + person[key]);
}
```

In this example, the loop will iterate over the properties of the `person` object and log the key-value pairs to the console.

> **Last reviewed**: November 28, 2025
