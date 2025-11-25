> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Spread

#javascript #programming #javascript #core-concepts

created: 1738969862385
updated: 1739906559064

---

<!--#region styles-->

<!--#endregion-->

# Spread Operator

The spread operator is a new addition to the set of operators in JavaScript ES6. It takes in an iterable (e.g an array) and expands it into individual elements. The spread operator is used to split up array elements or object properties.

The spread operator is denoted by three dots `...` and is used to expand an array or object into individual elements. It is used to copy the elements of an array or object into another array or object.

The spread operator is used in the following ways:

1. <b>Copying an array:</b> The spread operator is used to copy the elements of an array into another array.

2. <b>Concatenating arrays:</b> The spread operator is used to concatenate two or more arrays.

3. <b>Passing elements of an array as arguments:</b> The spread operator is used to pass the elements of an array as arguments to a function.
4. <b>Copying an object:</b> The spread operator is used to copy the properties of an object into another object.

#### Examples:

1.  <b>Copying an array:</b>

    ```javascript
    const arr = [1, 2, 3];
    const arr2 = [...arr]; // copies arr into arr2
    console.log(arr2); // Output: [1, 2, 3]
    ```

2.  <b>Concatenating arrays:</b>

    ```javascript
    const arr1 = [1, 2, 3];
    const arr2 = [4, 5, 6];
    const arr3 = [...arr1, ...arr2]; // concatenates arr1 and arr2 into arr3
    console.log(arr3); // Output: [1, 2, 3, 4, 5, 6]
    ```

3.  <b>Passing elements of an array as arguments:</b>

    ```javascript
    function sum(x, y, z) {
      return x + y + z;
    }
    const numbers = [1, 2, 3];
    console.log(sum(...numbers)); // Output: 6
    ```

4.  <b>Copying an object:</b>

    ```javascript
    const obj1 = { a: 1, b: 2 };
    const obj2 = { ...obj1, c: 3 }; // copies obj1 into obj2 and adds property c
    console.log(obj2); // Output: { a: 1, b: 2, c: 3 }
    ```

> **Last reviewed**: November 28, 2025
