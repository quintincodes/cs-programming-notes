> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Reduce

#javascript #programming #javascript #core-concepts

created: 1738708823732
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## Definition

`reduce()` is a method that executes a reducer function on each element of the array, resulting in a single output value. This method is used to reduce the array to a single value.

## Syntax

```js
array.reduce(callback(accumulator, currentValue, index, array), initialValue);
```

## Parameters

- `callback`: A function that is called on each element of the array. It takes four arguments:

  - `accumulator`: The accumulator accumulates the callback's return values. It is the accumulated value previously returned in the last invocation of the callback, or `initialValue`, if supplied.
  - `currentValue`: The current element being processed in the array.
  - `index`: The index of the current element being processed in the array.
  - `array`: The array `reduce()` was called upon.

## Return Values

The return value of the `reduce()` method is the accumulated value that results from the reduction. If no `initialValue` is provided, the first element in the array is used as the initial value. If the array is empty and no `initialValue` is provided, a `TypeError` is thrown. If the array has only one element and no `initialValue` is provided, the single element is returned without calling the callback function.

## Examples

### Example 1

```js
const numbers = [1, 2, 3, 4, 5];

const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue
);

console.log(sum); // Output: 15
```

## Applicable To

- arrays

## Edge Cases

- If the array is empty and no `initialValue` is provided, a `TypeError` is thrown.

## Links

- [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

> **Last reviewed**: November 28, 2025
