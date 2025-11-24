> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Arrays

#javascript #programming

created: 1733966144654
updated: 1738275940309

---

<!--#region styles-->

<!--#endregion-->

# Arrays In JavaScript

An array is a special variable that can hold more than one value at a time. It is a collection of variables that are stored under a single name. Each value in an array is called an element. eg. `var cars = ["Saab", "Volvo", "BMW"];`

## Creating an Array

You can create an array in the following ways:

1. Using an array literal: `var cars = ["Saab", "Volvo", "BMW"];` An array literal is a list of variables separated by commas and enclosed in square brackets.

2. Using the `Array()` constructor: `var cars = new Array("Saab", "Volvo", "BMW");` The `Array()` constructor is used to create an array.

3. Using the `Array.of()` method: `var cars = Array.of("Saab", "Volvo", "BMW");` The `Array.of()` method creates an array from a list of arguments.
4. Using the `Array.from()` method: `var cars = Array.from("Saab", "Volvo", "BMW");` The `Array.from()` method creates an array from an array-like or iterable object.
5. Using the `Array.isArray()` method: `Array.isArray(cars);` The `Array.isArray()` method checks if a value is an array.
6. Using the `Array.prototype` property: `Array.prototype;` The `Array.prototype` property represents the prototype for the `Array` constructor.
7. Using the `Array.prototype.concat()` method: `cars.concat(["Audi", "Mercedes"]);` The `concat()` method is used to merge two or more arrays.

## Accessing Array Elements

You can access an array element by referring to the index number. The index number starts from 0. eg. `var cars = ["Saab", "Volvo", "BMW"]; cars[0];` The first element in the array is `cars[0]`, the second element is `cars[1]`, and so on.

## Array Properties

1. `length`: The `length` property returns the number of elements in an array. eg. `cars.length;` The `length` property returns `3` for the array `cars = ["Saab", "Volvo", "BMW"];`.

2. `constructor`: The `constructor` property returns the constructor function for an array. eg. `cars.constructor;` The `constructor` property returns `Array()` for the array `cars = ["Saab", "Volvo", "BMW"];`.
3. `prototype`: The `prototype` property represents the prototype for the `Array` constructor. eg. `Array.prototype;` The `prototype` property returns the prototype for the `Array` constructor.
4. `isArray()`: The `isArray()` method checks if a value is an array. eg. `Array.isArray(cars);` The `isArray()` method returns `true` if the value is an array.
5. `from()`: The `from()` method creates an array from an array-like or iterable object. eg. `Array.from("Saab", "Volvo", "BMW");` The `from()` method creates an array from an array-like or iterable object.
6. `of()`: The `of()` method creates an array from a list of arguments. eg. `Array.of("Saab", "Volvo", "BMW");` The `of()` method creates an array from a list of arguments.
7. `concat()`: The `concat()` method is used to merge two or more arrays. eg. `cars.concat(["Audi", "Mercedes"]);` The `concat()` method is used to merge two or more arrays.
8. `copyWithin()`: The `copyWithin()` method copies array elements to another position in the array. eg. `cars.copyWithin(0, 1);` The `copyWithin()` method copies the elements from index `1` to the beginning of the array.
9. `entries()`: The `entries()` method returns an array iterator object with key/value pairs. eg. `cars.entries();` The `entries()` method returns an array iterator object with key/value pairs.
10. `every()`: The `every()` method checks if all elements in an array pass a test. eg. `cars.every(checkCar);` The `every()` method checks if all elements in the `cars` array pass the `checkCar` test function.
11. `fill()`: The `fill()` method fills the elements in an array with a static value. eg. `cars.fill("Toyota");` The `fill()` method fills all elements in the `cars` array with the value `"Toyota"`.
12. `filter()`: The `filter()` method creates a new array with elements that pass a test. eg. `cars.filter(checkCar);` The `filter()` method creates a new array with elements that pass the `checkCar` test function.
13. `find()`: The `find()` method returns the value of the first element in an array that passes a test. eg. `cars.find(checkCar);` The `find()` method returns the first element in the `cars` array that passes the `checkCar` test function.
14. `findIndex()`: The `findIndex()` method returns the index of the first element in an array that passes a test. eg. `cars.findIndex(checkCar);` The `findIndex()` method returns the index of the first element in the `cars` array that passes the `checkCar` test function.
15. `flat()`: The `flat()` method creates a new array with all sub-array elements concatenated into it recursively up to the specified depth. eg. `cars.flat();` The `flat()` method creates a new array with all sub-array elements concatenated into it.
16. `flatMap()`: The `flatMap()` method creates a new array by applying a function to each element in the array and then flattening the result by one level. eg. `cars.flatMap(getModels);` The `flatMap()` method creates a new array by applying the `getModels` function to each element in the `cars` array.
17. `forEach()`: The `forEach()` method calls a function for each array element. eg. `cars.forEach(displayCar);` The `forEach()` method calls the `displayCar` function for each element in the `cars` array.
18. `includes()`: The `includes()` method checks if an array contains a specified element. eg. `cars.includes("Volvo");` The `includes()` method returns `true` if the `cars` array contains the element `"Volvo"`.
19. `indexOf()`: The `indexOf()` method returns the index of the first occurrence of a specified element in an array. eg. `cars.indexOf("Volvo");` The `indexOf()` method returns `1` for the element `"Volvo"` in the `cars` array.
20. `join()`: The `join()` method joins all elements of an array into a string. eg. `cars.join(" - ");` The `join()` method joins all elements of the `cars` array into a string separated by `" - "`.

## Array Methods

1. `push()`: The `push()` method adds new elements to the end of an array. eg. `cars.push("Audi");` The `push()` method adds the element `"Audi"` to the end of the `cars` array.

2. `pop()`: The `pop()` method removes the last element from an array. eg. `cars.pop();` The `pop()` method removes the last element from the `cars` array.
3. `shift()`: The `shift()` method removes the first element from an array. eg. `cars.shift();` The `shift()` method removes the first element from the `cars` array.
4. `unshift()`: The `unshift()` method adds new elements to the beginning of an array. eg. `cars.unshift("Audi");` The `unshift()` method adds the element `"Audi"` to the beginning of the `cars` array.
5. `splice()`: The `splice()` method adds or removes elements from an array. eg. `cars.splice(1, 0, "Audi", "Mercedes");` The `splice()` method adds the elements `"Audi"` and `"Mercedes"` to the `cars` array at index `1`.
6. `slice()`: The `slice()` method returns selected elements from an array. eg. `cars.slice(1, 3);` The `slice()` method returns the elements from index `1` to `3` in the `cars` array.
7. `concat()`: The `concat()` method is used to merge two or more arrays. eg. `cars.concat(["Audi", "Mercedes"]);` The `concat()` method is used to merge two or more arrays.
8. `join()`: The `join()` method joins all elements of an array into a string. eg. `cars.join(" - ");` The `join()` method joins all elements of the `cars` array into a string separated by `" - "`.
9. `reverse()`: The `reverse()` method reverses the order of the elements in an array. eg. `cars.reverse();` The `reverse()` method reverses the order of the elements in the `cars` array.
10. `sort()`: The `sort()` method sorts the elements of an array. eg. `cars.sort();` The `sort()` method sorts the elements of the `cars` array alphabetically.

> **Last reviewed**: November 28, 2025
