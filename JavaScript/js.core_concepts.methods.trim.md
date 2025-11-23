> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Trim

#javascript #programming #javascript #core-concepts

created: 1736972360164
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## Definiton

The `trim()` method removes whitespace from both ends of a string. Whitespace in this context is all the whitespace characters (space, tab, no-break space, etc.) and all the line terminator characters (LF, CR, etc.).

## Syntax

```js
str.trim();
```

## Parameters

None

## Return value

A new string representing the calling string stripped of whitespace from both ends.

## Examples

```js
console.log("   foo  ".trim()); // 'foo'
```

## Applicable To

The trim method is applicable to all strings.

## Edge cases

```js
console.log("   foo  ".trim()); // 'foo'
console.log("foo".trim()); // 'foo'
console.log("".trim()); // ''
```

## Links

- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/trim)

> **Last reviewed**: November 28, 2025
