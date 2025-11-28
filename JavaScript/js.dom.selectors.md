> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: Selectors

#javascript #programming

created: 1738359449554
updated: 1738364562767

---

<!--#region styles-->

<!--#endregion-->

# DOM API METHODS

## 1. querySelector()

The `querySelector()` method returns the first element that matches a specified CSS selector(s) in the document.

```js
document.querySelector(selector);
```

#### Example:

```js
const paragraph = document.querySelector("p");

/* The above code will return the first paragraph element in the document and 
assign it to the variable 'paragraph'. */
```

## 2. querySelectorAll()

The `querySelectorAll()` method returns all elements in the document that matches a specified CSS selector(s), as a static NodeList object.

```js
document.querySelectorAll(selector);
```

#### Example:

```js
const paragraphs = document.querySelectorAll("p");

/*The above code will return a static NodeList of all paragraph elements in the document and
 assign it to the variable 'paragraphs'.*/
```

> **Note💡:** The `querySelectorAll()` method returns a static NodeList, which means that any changes made to the document will not be reflected in the NodeList.

## 3. getElementById()

The `getElementById()` method returns the element that has the ID attribute with the specified value.

```js
document.getElementById(id);
```

#### Example:

```js
const myElement = document.getElementById("myId");

/*The above code will return the element with the ID 'myId' and
 assign it to the variable 'myElement'.*/
```

## 4. getElementsByClassName()

The `getElementsByClassName()` method returns a collection of all elements in the document with the specified class name.

```js
document.getElementsByClassName(className);
```

#### Example:

```js
const myElements = document.getElementsByClassName("myClass");

/*The above code will return all elements with the class 'myClass' and
 assign them to the variable 'myElements'.*/
```

## 5. getElementsByTagName()

The `getElementsByTagName()` method returns a collection of all elements in the document with the specified tag name.

```js
document.getElementsByTagName(tagName);
```

#### Example:

```js
const myElements = document.getElementsByTagName("p");

/*The above code will return all paragraph elements in the document and
 assign them to the variable 'myElements'.*/
```

## 6. getElementsByName()

The `getElementsByName()` method returns a collection of all elements in the document with the specified name attribute.

```js
document.getElementsByName(name);
```

#### Example:

```js
const myElements = document.getElementsByName("myName");

/*The above code will return all elements with the name 'myName' and
 assign them to the variable 'myElements'.*/
```

> **Last reviewed**: November 28, 2025
