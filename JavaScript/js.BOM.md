> **Note**: This note contained custom CSS styling. Check the CSS snippets in Obsidian settings.

---

## title: BOM

#javascript #programming #javascript #browser

created: 1741488886729
updated: 1732750000000

---

> Last reviewed: 2025-11-28

<!--#region styles-->

<!--#endregion-->

## BOM (Browser Object Model)

The Browser Object Model (BOM) is a collection of objects that allow JavaScript to interact with the browser. It provides methods and properties to manipulate the browser window, including the ability to open new windows, navigate to different URLs, and manage browser history.

### Key Components of BOM

- **Window Object**: Represents the browser window and provides methods to control it.
- **Navigator Object**: Contains information about the browser and the operating system.
- **Screen Object**: Provides information about the user's screen, such as its width and height.
- **Location Object**: Represents the current URL and provides methods to manipulate it.
- **History Object**: Allows access to the browser's session history, enabling navigation through previously visited pages.
-
- **Document Object**: Represents the HTML document loaded in the browser and provides methods to manipulate its content.
- **XMLHttpRequest Object**: Used for making asynchronous HTTP requests to the server, enabling dynamic content loading without refreshing the page.
-
- **Console Object**: Provides methods for logging messages to the browser's console, useful for debugging and testing.
- **Alert, Confirm, and Prompt Dialogs**: Methods for displaying alert messages, confirmation dialogs, and input prompts to the user.
- **Timers**: Functions like `setTimeout` and `setInterval` for scheduling code execution after a specified delay or at regular intervals.
- **Geolocation API**: Provides access to the user's geographical location, allowing for location-based services.

### Example of Using BOM

```javascript
// Open a new window
var newWindow = window.open("https://www.example.com", "_blank");
// Get the current URL
var currentURL = window.location.href;
console.log("Current URL: " + currentURL);
// Get the screen width and height
var screenWidth = window.screen.width;
var screenHeight = window.screen.height;
```

```javascript
// Get the browser name and version
var browserName = window.navigator.appName;
var browserVersion = window.navigator.appVersion;
console.log("Browser Name: " + browserName);
console.log("Browser Version: " + browserVersion);
// Get the user's screen width and height
```

> **Last reviewed**: November 27, 2025
