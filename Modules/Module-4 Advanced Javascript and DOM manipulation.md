# Internet and Web Programming (ITA6003)

## Module 4 : Advanced Javascript and DOM manipulation

- [x] ~~Browser Object Model~~
- [x] ~~Window Object~~
- [x] ~~open()~~
- [x] ~~setTimeout()~~
- [x] ~~History Object~~
- [x] ~~Navigator Object~~
- [x] ~~Screen Object~~
- [x] ~~Document Object Model~~
- [x] ~~Document Object Model Methods~~
- [x] ~~Form Validation~~

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
- Set Interval allows us to repeatedly do something after a fixed interval of time.

```js
// Set Timeout
console.log("This prints immediately");

setTimeout(function () {
  console.log("This is after 3 sec");
}, 3000);

// Set Interval
console.log("This prints immediately");

setInterval(function () {
  console.log("This gets printed every 1 sec");
}, 1000);


// Open
open("https://www.google.co.in");
```

## Document Object Model

- When we get an element using tagname or class, it will give us an array of elements, so if you want to change the innner text or html, use the subscript to get the right element and change it.

```js
// Write
document.write("This is written by js");

// Write Line
document.writeln("This is written by js in a new line");

// Get element by id
let emailText = document.getElementById("emailText");

// Get element by class name
let spinner = document.getElementsByClassName("spinner");

// Get element by tag name
let span = document.getElementsByTagName("span");

// Inner Text
let thing = document.getElementsByClassName("thing");
thing[0].innerText = "This is it!";

// Inner HTML
let thing = document.getElementsByClassName("thing");
thing[0].innerHTML = "This is it!";

// Classlist toggle
const toggle = () => thing.classList.toggle("hidden");

// Get input value
let inputText = document.getElementById("input").value;
```

## Form Validation

### HTML Form

```html
Name : <input required type="text" id="name" /> <br />

Email : <input required type="email" id="email" /> <br />

Password : <input required type="password" id="password" /> <br />

Confirm Password : <input required type="password" id="repassword" /> <br />

Age : <input required type="number" id="age" /> <br />

Gender :
<fieldset>
  Male <input checked name="age" value="male" class="gender" type="radio" /> 
  Female <input name="age" value="female" class="gender" type="radio" />
</fieldset>
<br />

<button onclick="validate()">Validate!</button>
```

### Javascript Validation

```js
function validate() {
  // Declare objects
  let name = document.getElementById("name").value;
  let email = document.getElementById("email").value;
  let password = document.getElementById("password").value;
  let repassword = document.getElementById("repassword").value;
  let age = document.getElementById("age").value;

  // Validate using Regex
  name = /^[a-zA-Z ]*$/.test(name) ? true : false;
  email = /[a-zA-Z0-9]+@[a-z]+\.[a-z]{2,3}/.test(email) ? true : false;
  repassword = password == repassword ? true : false;
  password = /[a-zA-Z0-9@#$%!_\-.]{8,}/.test(password) ? true : false;
  age = age > 18 && age < 100 ? true : false;

  alert(name && email && password && repassword && age ? "Valid" : "Invalid");
}
```
