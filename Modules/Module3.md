# Internet and Web Programming (ITA6003)

## Module 3 : Basics of Javascript

- [x] ~~Introduction to JS~~
- [x] ~~Features of JavaScript~~
- [x] ~~Applications of JavaScript~~
- [x] ~~Variables~~
- [x] ~~Data Types~~
- [x] ~~Operators~~
- [x] ~~If else~~
- [x] ~~Switch~~
- [x] ~~Loops~~
- [x] ~~Functions~~
- [x] ~~Objects~~
- [x] ~~Arrays~~
- [x] ~~Array Methods~~
- [x] ~~Strings~~
- [x] ~~Strings Methods~~
- [x] ~~Date~~
- [x] ~~Date Methods~~

## Introduction to JS

- Lightweight object oriented language
- Used for web scripting
- Dynamic Interaction on websites without page reload
- Introduced in 1995

## Features of JS

- C-like structured syntax
- Weakly typed language with implicit casting
- Uses prototypal inheritance
- Lightweight and interpreted

## Applications of JavaScript

- Client side validation
- Dynamic drop down menus
- Displaying date and time
- Display popup windows and dialog boxes

## Variables

- Name of a storage location which holds some value
- It can be local or global
- Local variables - Declared inside the scope
- Global variables - Declared outside the scope
- Naming starts with `a-z` or `A-Z` or `_` or `$`.
- After the characters mentioned above, we can use `0-9`
- Identifiers are case sensitive.

## Data Types

- There are 2 main types : Primitive and Reference types.
- Primitive contains :
  - `String` : Represents sequence of characters
  - `Number` : Represents numeric values
  - `Boolean` : Represents boolean value either false or true
  - `Undefined` : Represents undefined value
  - `Null` : Represents null i.e. no value
- Non-primitives contain :
  - `Object` : Instance through which we can access members
  - `Array` : Group of homogeneous values
  - `RegExp` : Represents regular expression

## Operators

- Symbols for performing operations on the operands
- Following operators are present in JavaScript:
  - Arithmetic Operators : `+`, `-`, `*`, `/`, `%`.
  - Comparison Operators : `==`, `!=`, `<`, `>`, `>=`, `<=`.
  - Bitwise Operators : `<<`, `>>`, `>>>`, `&`, `|`, `^`, `~`.
  - Logical Operators : `&&`, `||`, `!`.
  - Assignment Operators : `=`, `+=`, `-=`, `*=`, `/=`, `%=`.
  - Special Operators : `(?:)`, `,`, `delete`, `in`, `instanceOf`, `new`, `typeOf`.

## If else

- Execute a certain block of code when a condition or alternating conditions holds true

```javascript
if (condition) {
  // Statements
} else if (condition) {
  // Statements
} else {
  // Statements
}
```

## Switch

- Execute a block of code when a case expression holds true

```javascript
switch (expression) {
  case value1:
    // statements
    break;
  case value2:
    // statements
    break;
  default:
  // statements
}
```

## Loops

- They execute a piece of code repeatedly until either the certain number of times, or till the condition is true.
- Could be a for loop, while loop, do while loop, for-of loop, or a for-in loop.
- For in is used to iterate over the members of the object.

```javascript
// For loop
for (init; condition; increment) {
  // statements
}

// For-in Loop
for (key in object) {
  // Statements
}

// For of loop
for (let item of arr) {
}

// While loop
while (condition) {
  // Statements
}

// Do While
do {
  // Statements
} while (condition);
```

## Functions

- It is a block of code designed to perform a particular task.
- It can receive certain values as arguments and can return a value.
- A function is executed when "something" invokes it (calls it).

```javascript
function multiply(p1, p2) {
  return p1 * p2;
}
```

## Objects

- It is an entity having properties and method.
- Everything is an object in JavaScript
- JS is template based, we don't use classes to create objects, we instead, directly create objects.
- Object is created in 3 different ways:

  ### 1. Object literal

  ```javascript
  myObj = {
    property1: "value1",
    property2: "value2",
  };

  alert(myObj.property1 + " " + myObj.property2);
  ```

  ### 2. Creating instance of object using `new` Keyword.

  ```javascript
  let obj = new Object();
  obj.property1 = "value1";

  alert(myObj.property1);
  ```

  ### 3. By using object cosntructor using `new` Keyword.

  ```javascript
  function obj(property1, property2) {
    this.property1 = property1;
    this.property2 = property2;
  }

  let myObj = new obj("Value1", "Value2");

  alert(myObj.property1 + " " + myObj.property2);
  ```

## Arrays

- Stores homogeneous elements
- Size of the array is Dynamic (it can grow or shrink)
- Index starts from 0

```js
// Create a simple array
let arr = [1, 2, 3];

// Creating array using Array Constructor
let arr = new Array(1, 2, 3);

// Create array using Object
let arr;
arr[0] = value;
arr[1] = value;
arr[2] = value;
```

## Array Methods

```js

// Add or remove elements

arr.push(..items);              // Adds values at the end of the array.
arr.pop();                      // Remove value at the end of the array.
arr.shift();                    // Remove the value at the start of the array.
arr.unshift(..items);           // Add the value at the start of the array.
arr.splice(start, n, ..items);  // From start, remove n elements and replace them with ..items.
arr.concat([arr2]);             // Concatenate the arr2 at the end of arr.


// Return Elements

arr.slice(start, end);          // Returns new array with elements from start index and before end index
arr.indexOf(item, pos);         // look for item starting from position pos, return the index or -1 if not found.
arr.lastIndexOf(item, pos);     // look for item starting from position pos, return the index or -1 if not found.
arr.includes(item);             // Returns true if array contains item.
arr.reverse();                  // Reverses array and returns it.


// Iterate over the elements

arr.forEach(function(item, index, array) {
  // ... do something with item, index and array
});
// arr.forEach(item => alert(item));

let result = arr.find(function(item, index, array) {
  // if true is returned, item is returned and iteration is stopped
  // for falsy scenario returns undefined
});
// let res = arr.find(item => item % 2 == 0);

let result = arr.filter(function(item, index, array) {
  // if true item is pushed to result and the iteration continues
  // returns empty array if nothing found
});
// let res = arr.filter((item, index, arr) => item % 2 != 0)

let result = arr.map(function(item, index, array) {
  // returns the new value instead of item
});
// let res = arr.map((item) => 13 * item)


// Sorting the array

arr.sort();             // Performs sorting as if the items were strings
arr.sort((a,b) => a-b); // Performs numeric sorting in ascending order
arr.sort((a,b) => b-a); // Performs numeric sorting in descending order


// Split string into array
let arr = str.split("delim");
```

## Strings Methods

```js
let str = "this is a string";

// Get the char at index

console.log(str[0]);
console.log(str.charAt(0));

// Iterate over each character in the array
for (char of str) {
  console.log(char);
}

// Changing the case

console.log(str.toLowerCase());
console.log(str.toUpperCase());

// Find elements

console.log(str.indexOf("is")); // 2
console.log(str.includes("is")); // True
console.log(str.startsWith("T")); // False
console.log(str.endsWith("g")); // True

// Substrings

console.log(str.slice(0, 5)); // 'this '
console.log(str.substring(2, 4)); // 'is'

// Trim Spaces

console.log(str.trim());
console.log(str.repeat(2));
```

## Date

```js
// Create a new Date object
let now = new Date();

// Getting date details

console.log(now); // 2022-06-04T10:05:28.496Z
console.log(now.getDate()); // Day (from 1 to 31)
console.log(now.getMonth()); // Month (starting from 0 to 11)
console.log(now.getFullYear()); // Year (2022)

console.log(now.getHours()); // Hours
console.log(now.getMinutes()); // Minutes
console.log(now.getSeconds()); // Seconds

// Setting Date Details

now.setDate(13); // Day (from 1 to 31)
now.setMonth(10); // Month (starting from 0 to 11)
now.setFullYear(2049); // Year (2022)

now.setHours(2); // Hours
now.setMinutes(0); // Minutes
now.setSeconds(0); // Seconds

// Creating a date from constructor
let year = 2049;
let month = 10;
let day = 13;
let hr = 2;
let min = 15;
let sec = 20;
let ms = 33;
let date = new Date(year, month, day, hr, min, sec, ms);
console.log(date);
```
