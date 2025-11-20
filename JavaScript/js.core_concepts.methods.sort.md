> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Sort

#javascript #programming #javascript #core-concepts

created: 1736370797095
updated: 1738275940326

---

<!--#region styles-->

<!--#endregion-->

## Definition

The `sort()` method sorts the elements of an array in place and returns the sorted array. The default sort order is ascending, built upon converting the elements into strings, then comparing their sequences of UTF-16 code units values.

## Syntax

```js
arr.sort([compareFunction]);
```

where `compareFunction` is an optional parameter that specifies a function that defines the sort order. If omitted, the array elements are converted to strings, then sorted according to each character's Unicode code point value.

## Parameters

- `compareFunction` (Optional) - Specifies a function that defines the sort order. If omitted, the array is sorted according to each character's Unicode code point value.

## Return Values

- The sorted array.

## Examples

### Example 1

```js
const months = ["March", "Jan", "Feb", "Dec"];
months.sort();
console.log(months);
// expected output: Array ["Dec", "Feb", "Jan", "March"]
```

in this example, the array is sorted alphabetically, with the default sort order being ascending.

### Example 2

```js
const array1 = [1, 30, 4, 21, 100000];
array1.sort();
console.log(array1);
// expected output: Array [1, 100000, 21, 30, 4]
```

in this example, the array is sorted as strings, so the default sort order is not correct. The reason this array was sorted as strings is that the `compareFunction` parameter was not provided.

## Applicable To

- JavaScript Arrays
- JavaScript Typed Arrays

## Edge Cases

### Edge Case 1

```js
const array1 = [1, 30, 4, 21, 100000];
array1.sort((a, b) => a - b);
console.log(array1);
// expected output: Array [1, 4, 21, 30, 100000]
```

in this example, the array is sorted numerically, with the `compareFunction` parameter provided. this is an edge case because the array is sorted numerically, not alphabetically which is due to the `compareFunction` parameter.

### Edge Case 2

```js
const array1 = [1, 30, 4, 21, 100000];
array1.sort((a, b) => b - a);
console.log(array1);
// expected output: Array [100000, 30, 21, 4, 1]
```

in this example, the array is sorted numerically in descending order, with the `compareFunction` parameter provided. this is an edge case because the array is sorted numerically in descending order, not alphabetically which is due to the `compareFunction` parameter.

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)
- [JavaScript.info](https://javascript.info/array-methods#sort)

> **Last reviewed**: November 28, 2025
