> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: forEach

#javascript #programming #javascript #core-concepts

created: 1737650770269
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## Definition

The `forEach()` method executes a provided function once for each array element.

## Syntax

```js
array.forEach(function(currentValue, index, arr), thisValue)


```

## Parameters

- `currentValue`: The current element being processed in the array.

- `index`: The index of the current element being processed in the array.
- `arr`: The array `forEach()` was called upon.
- `thisValue`: A value to be passed to the function to be used as its "this" value.
- `function`: A function to execute for each element, taking three arguments:
  - `currentValue`: The current element being processed in the array.
  - `index`: The index of the current element being processed in the array.
  - `arr`: The array `forEach()` was called upon.

## Return Values

The `forEach()` method does not return anything.

## Examples

### Basic Example

```js
const array1 = ["a", "b", "c"];

array1.forEach((element) => console.log(element));
// Output: a, b, c
```

### Using All Parameters

```js
const fruits = ["apple", "banana", "cherry"];

fruits.forEach((fruit, index, array) => {
  console.log(`${index}: ${fruit} (total: ${array.length})`);
});

// Output:
// 0: apple (total: 3)
// 1: banana (total: 3)
// 2: cherry (total: 3)
```

### Arrow Function vs Regular Function

```js
const numbers = [1, 2, 3];

// Arrow function
numbers.forEach((num) => console.log(num * 2));

// Regular function
numbers.forEach(function (num) {
  console.log(num * 2);
});
```

### Modifying Elements During Iteration

```js
const prices = [10, 20, 30];

prices.forEach((price, index, arr) => {
  arr[index] = price * 1.1; // Add 10% tax
});

console.log(prices); // [11, 22, 33]
```

### Using thisValue Parameter

```js
const calculator = {
  multiplier: 5,
  multiplyArray: function (arr) {
    arr.forEach(function (num) {
      console.log(num * this.multiplier);
    }, this); // Pass calculator object as 'this'
  },
};

calculator.multiplyArray([1, 2, 3]); // 5, 10, 15
```

## Applicable To

The `forEach()` method is applicable to all arrays.

## Edge Cases

- If the array is modified during iteration, other elements might be skipped.
- If the array is sparse, the index will not be visited for those elements.

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

> **Last reviewed**: November 28, 2025
