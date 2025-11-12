> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Join

#javascript #programming #javascript #core-concepts

created: 1737412676490
updated: 1738275940340

---

<!--#region styles-->

<!--#endregion-->

## Definition

The `join()` method creates and returns a new string by concatenating all of the elements in an array (or an array-like object), separated by commas or a specified separator string. If the array has only one item, then that item will be returned without using the separator.

## Syntax

```js
arr.join([separator]);
```

## Parameters

- `separator` (Optional): Specifies a string to separate each element of the array. The separator is converted to a string if necessary. If omitted, the array elements are separated with a comma. If separator is an empty string, all elements are joined without any characters in between them. If separator is not provided, elements are separated with a comma.

## Return Values

A string representing the elements of the array, separated by the specified separator. If the array has no elements or if the separator is an empty string, the result is an empty string.

## Examples

```js
const fruits = ["apple", "banana", "mango", "orange"];
const result = fruits.join();
console.log(result); // Output: 'apple,banana,mango,orange'
```

## Applicable To

The `join()` method is applicable to all JavaScript arrays.

## Edge Cases

### Edge Case 1

If the array has only one item, then that item will be returned without using the separator.

```js
const fruits = ["apple"];
const result = fruits.join();
console.log(result); // Output: 'apple'
```

### Edge Case 2

If the array has no elements, the result is an empty string.

```js
const fruits = [];
const result = fruits.join();
console.log(result); // Output: ''
```

## Links

- [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

> **Last reviewed**: November 28, 2025
