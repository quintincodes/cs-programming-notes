> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Split

#javascript #programming #javascript #core-concepts

created: 1736634481961
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## Definition

The `split()` method is used to split a string into an array of substrings, and returns the new array. The method takes two parameters: a separator and an optional limit. The separator is used to specify where to split the string, and the limit is used to specify the maximum number of splits to make.

## Syntax

```js
string.split(separator, limit);
```

## Parameters

- `separator`: The separator to use when splitting the string. This can be a string or a regular expression. If the separator is an empty string, the string is split into an array of each character. If the separator is omitted, the entire string is returned as the first element of the array. The separator is case-sensitive.

- `limit`: An optional parameter that specifies the maximum number of splits to make. If the limit is provided, the resulting array will have a maximum length of limit - 1. If the limit is not provided, the entire string is split. If the limit is 0, the method returns an empty array.

## Examples

### Basic String Splitting

```js
const sentence = "Hello,World,JavaScript";
const words = sentence.split(",");
console.log(words); // ['Hello', 'World', 'JavaScript']

const phrase = "apple banana cherry";
const fruits = phrase.split(" ");
console.log(fruits); // ['apple', 'banana', 'cherry']
```

### Splitting with Limit Parameter

```js
const text = "one,two,three,four,five";
const limited = text.split(",", 3);
console.log(limited); // ['one', 'two', 'three']

const url = "https://www.example.com/path/to/page";
const parts = url.split("/", 3);
console.log(parts); // ['https:', '', 'www.example.com']
```

### Splitting into Individual Characters

```js
const word = "hello";
const characters = word.split("");
console.log(characters); // ['h', 'e', 'l', 'l', 'o']

const text = "JavaScript";
const chars = text.split("");
console.log(chars.length); // 10
```

### Using Regular Expressions as Separator

```js
const text = "apple123banana456cherry";
const fruits = text.split(/\d+/);
console.log(fruits); // ['apple', 'banana', 'cherry']

const sentence = "Hello   world    JavaScript";
const words = sentence.split(/\s+/); // Split on one or more whitespace
console.log(words); // ['Hello', 'world', 'JavaScript']
```

### Splitting File Paths and URLs

```js
const filePath = "/home/user/documents/file.txt";
const pathParts = filePath.split("/");
console.log(pathParts); // ['', 'home', 'user', 'documents', 'file.txt']

const url = "https://api.example.com/users/123/profile";
const urlParts = url.split("/");
console.log(urlParts); // ['https:', '', 'api.example.com', 'users', '123', 'profile']
```

### Parsing CSV Data

```js
const csvData = "name,age,city\nJohn,25,New York\nJane,30,Los Angeles";
const lines = csvData.split("\n");
console.log(lines);
// ['name,age,city', 'John,25,New York', 'Jane,30,Los Angeles']

const headers = lines[0].split(",");
const firstRow = lines[1].split(",");
console.log(headers); // ['name', 'age', 'city']
console.log(firstRow); // ['John', '25', 'New York']
```

### Splitting Email Addresses

```js
const email = "user@example.com";
const emailParts = email.split("@");
console.log(emailParts); // ['user', 'example.com']

const [username, domain] = email.split("@");
console.log(username); // 'user'
console.log(domain); // 'example.com'
```

### Processing Form Data

```js
const formData = "name=John&age=25&city=NewYork";
const pairs = formData.split("&");
console.log(pairs); // ['name=John', 'age=25', 'city=NewYork']

const data = {};
pairs.forEach((pair) => {
  const [key, value] = pair.split("=");
  data[key] = value;
});
console.log(data); // {name: 'John', age: '25', city: 'NewYork'}
```

### Working with Sentences and Paragraphs

```js
const paragraph =
  "This is sentence one. This is sentence two! This is sentence three?";
const sentences = paragraph.split(/[.!?]/).filter((s) => s.trim() !== "");
console.log(sentences);
// ['This is sentence one', ' This is sentence two', ' This is sentence three']

const text = "First paragraph.\n\nSecond paragraph.\n\nThird paragraph.";
const paragraphs = text.split("\n\n");
console.log(paragraphs);
// ['First paragraph.', 'Second paragraph.', 'Third paragraph.']
```

### Practical Applications

#### Creating Breadcrumb Navigation

```js
function createBreadcrumb(path) {
  const parts = path.split("/").filter((part) => part !== "");
  return parts.map((part, index) => ({
    name: part,
    path: "/" + parts.slice(0, index + 1).join("/"),
  }));
}

const breadcrumb = createBreadcrumb("/products/electronics/smartphones");
console.log(breadcrumb);
// [
//   { name: 'products', path: '/products' },
//   { name: 'electronics', path: '/products/electronics' },
//   { name: 'smartphones', path: '/products/electronics/smartphones' }
// ]
```

#### Parsing Command Line Arguments

```js
function parseCommand(command) {
  const parts = command.trim().split(/\s+/);
  return {
    command: parts[0],
    args: parts.slice(1),
  };
}

const cmd = parseCommand('git commit -m "Initial commit"');
console.log(cmd);
// { command: 'git', args: ['commit', '-m', '"Initial', 'commit"'] }
```

## Edge Cases

### Empty String and No Separator

```js
const empty = "";
console.log(empty.split(",")); // ['']
console.log(empty.split("")); // []

const text = "hello";
console.log(text.split("")); // ['h', 'e', 'l', 'l', 'o']
console.log(text.split()); // ['hello']
```

### Separator Not Found

```js
const text = "hello world";
const result = text.split(",");
console.log(result); // ['hello world']
```

### Multiple Consecutive Separators

```js
const text = "a,,b,,,c";
const result = text.split(",");
console.log(result); // ['a', '', 'b', '', '', 'c']

// To remove empty strings
const filtered = result.filter((item) => item !== "");
console.log(filtered); // ['a', 'b', 'c']
```

### Limit Edge Cases

```js
const text = "a,b,c,d,e";
console.log(text.split(",", 0)); // []
console.log(text.split(",", 1)); // ['a']
console.log(text.split(",", 100)); // ['a', 'b', 'c', 'd', 'e']
```

This example demonstrates various uses of the `split()` method to divide strings into arrays based on different separators and patterns, making it essential for text processing, data parsing, and string manipulation tasks.

## Applicable To

The `split()` method is applicable to all JavaScript strings.

## Return Values

- The `split()` method returns an array of substrings. If the string is empty, the method returns an array with one empty string as the only element.

- If the separator is an empty string, the method returns an array of each character in the string.
- If the separator is not found in the string, the method returns an array with the entire string as the only element.
- If the limit is 0, the method returns an empty array.
- If the limit is not provided, the method returns an array with all the splits.
- If the limit is greater than the number of splits, the method returns an array with all the splits.

## Edge Cases

- If the separator is not found in the string, the method returns an array with the entire string as the only element. For example, `str.split('!')` will return `['Hello,World,JavaScript']`.
- If the separator is an empty string, the method returns an array of each character in the string. For example, `str.split('')` will return `['H', 'e', 'l', 'l', 'o', ',', 'W', 'o', 'r', 'l', 'd', ',', 'J', 'a', 'v', 'a', 'S', 'c', 'r', 'i', 'p', 't']`.
-

## Links

- [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/split)
- [W3Schools](https://www.w3schools.com/jsref/jsref_split.asp)
- [JavaScript.info](https://javascript.info/array-methods#split)
- [Can I Use](https://caniuse.com/?search=split)

> **Last reviewed**: November 28, 2025
