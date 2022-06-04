# Internet and Web Programming (ITA6003)

- [x] Browser Object Model
- [x] Window Object
- [x] open()
- [x] setTimeout()
- [x] History Object
- [x] Navigator Object
- [x] Screen Object
- [x] Document Object Model
- [ ] Document Object Model Methods
- [ ] Form Validation

## Browser Object Model

- Allows JavaScript to "talk to" the browser.
- No official standards for the Browser Object Model (BOM).

## Window Object

- The window object is supported by all browsers. It represents the browser's window.
- All global JavaScript objects, functions, and variables automatically become members of the window object.
- Global variables are properties of the window object.
- Global functions are methods of the window object.

```js
// Inner dimensions of the browser window
let height = window.innerHeight;
let width = window.innerWidth;

// Window methods are
window.open();
window.close();
window.moveTo();
window.resizeTo();

// Screen Object
console.log(screen); // Same as console.log(window.screen);
console.log(screen.width); // Width of the viewport
console.log(screen.height); // Height of the viewport
console.log(screen.availWidth); // Total available width of the viewport
console.log(screen.availHeight); // Total available height of the viewport
console.log(screen.colorDepth); // Color depth of the screen
console.log(screen.pixelDepth); // Same as Pixel color

// Window location
window.location.href; // returns the href (URL) of the current page
window.location.hostname; // returns the domain name of the web host
window.location.pathname; // returns the path and filename of the current page
window.location.protocol; // returns the web protocol used (http: or https:)
window.location.assign(); // loads a new document

// History
history.back(); // Same as clicking back in the browser
history.forward(); // Same as clicking forward in the browser
history.go(2); // Go forward 2 pages
history.go(-2); // Go backward 2 pages

// Navigator
navigator.appName; // Application name of the browser
navigator.appCodeName; // Object contains information about the visitor's browser.
navigator.platform; // Operating system and Platform
```

## Set Timeout and Open

- Set Timeout Allows us to execute some code after time specified.
- Open allows us to open some url in a new tab

```js
// Set Timeout
console.log("This prints immediately");

setTimeout(function () {
  console.log("This is after 3 sec");
}, 3000);


// Open
open("https://www.google.co.in");
```

## Document Object Model

```js
// Write
document.write("This is written by js");

// Write Line
document.writeln("This is written by js in a new line");

// Get element by id
let emailText = document.getElementById("emailText");

// Get element by class name
let spinner = document.getElementByClassName("spinner");

// Get element by tag name
let span = document.getElementByTagName("span");

// Inner Text


// Inner HTML

// Classlist toggle

// Get input value

```

## Form Validation
