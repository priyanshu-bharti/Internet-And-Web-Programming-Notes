# Internet and Web Programming (ITA6003)

## Module 5 : Introduction to PHP and Server Side Scripting

- [x] ~~PHP Introduction~~
- [x] ~~PHP Operators~~
- [x] ~~PHP Datatypes~~
- [x] ~~PHP Loops~~
- [x] ~~PHP Conditionals~~
- [x] ~~PHP Strings~~
- [x] ~~PHP Arrays~~
- [x] ~~Cookies~~
- [x] ~~Sessions~~
- [x] ~~Functions~~
- [x] ~~Math Functions~~

## PHP Introduction

- Stands for "**PHP: Hypertext Preprocessor**"
- Open Source, Genearl Purpose Scripting Language.
- Can be embedded in HTML.
- Server Side Language.
- PHP Scripts are executed on servers
- Supports many SQL and similar databases.
- Compatible with almost all kinds of servers today.
- It is loosely typed.

## PHP variables

- Variables can be static, global or local (depending on the scope).
- Static variables retain the value even when they're out of scope.
- To declare static variables, use `static` keyword.
- There are also regular and reference variables.
- `$` is used to declare regular variables, while `$$` is used to declare reference variables.

```php
$var = "India";
$$var = "Delhi";
echo $var . "'s capital " . $$var; // India's capital Delhi
echo $var . "'s capital " . $India; // India's capital Delhi
```

## PHP Constants

- Constants have a fixed value that can't be changed.
- They can be defined in 2 ways: either using `const` keyword or using `define()` method

```php
const PI = 3.14; // Method 1
define("PI", 3.14) // Method 2

// Printing the values
echo PI;
echo constant("PI");
```

## PHP Operators

1. **Arithmetic** : `+`, `-`, `*`, `/`, `%`, `++`, `--`.
1. **Assignment** : `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `.= (concat equals)`.
1. **Comparison** : `==`, `!=`, `>`, `<`, `>=`, `<=`, `<> (isn't equal)`.
1. **Logical** : `&&`, `||`, `!`.

## PHP Datatypes

There are 3 kinds of datatypes: Scalar, compound and special.

1. `Scalar` **String** : Sequence of characters
1. `Scalar` **Integer** : Non decimal value
1. `Scalar` **Float** : Decimal Values
1. `Scalar` **Boolean** : True/False
1. `Compound` **Array** : Collection of homogeneous values
1. `Compound` **Object** : Instance of a template class (with their properties)
1. `Special` **NULL** : Has no value at all
1. `Special` **Resource** : Stores reference of functions and resources external to PHP

## PHP Loops

PHP has the following types of loops:

1. For Loop
1. Foreach
1. While
1. Do While

```php
// For Loop
for (initialization; condition; increment) {
  // statements
}


// Foreach
for ($array as $value) {
  // statements
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

## PHP Conditionals

There can be 3 kinds of conditionals:

1. If else blocks
2. Switch Blocks
3. Ternary Statements

```php
// If Else Block

if (condition) {
  // statement
} else if (condition) {
  // statement
} else {
  // statement
}


// Switch Statements

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


// Ternary Operators

(condition expression) ? "True value" : "False Value";
```

## PHP Strings

```php
$str = "ThisisaString"; // Declaring a String

// Length
strlen($str); // Returns the length of the string
str_word_count($str) // Returns the number of words in a string


// Finding something
strpos($str, "SubString") // Returns the position of the substring else returns false
substr($a, 8, 5); // From $a, starting at position 8, extract 5 characters.


// Manipulating strings
strrev($str); // Returns the reverse of the string
str_replace($original, $replacement, $str); // Replaces some characters with others
$a . $b; // Concat Strings


// Comparison
strcmp($a, $b); // Compares strings and returns 0 when equal, 1 when a > b and -1 when a < b.


// Changing the case of string
ucwords($str); // Applies Uppercase to only words.
strtoupper($str); // Converts string to uppercase.
strtolower($str); // Converts string to lowercase.
```

## PHP Arrays

- Arrays are collection of similar elements.

```php
// Method 1 of creation
$numbers = array( 1, 2, 3, 4, 5);


// Method 2 of creation
$numbers[0] = "one";
$numbers[1] = "two";
$numbers[2] = "three";


// Checking array
is_array($arr); // Returns true if $arr is an array.


// Adding or Removing Elements
array_merge($arr1, $arr2); // Merges the arrays
array_push($arr, $toBePushed); // Pushes the elements to be pushed into the array.
array_pop($arr); // Removes the last element from the array.
array_shift($arr); // Removes and returns the first element from the array.
array_unshift($arr, 'value'); // Removes and returns the first element from the array.


// Finding element
in_array("value", $arr) // Returns true if value is present in $arr.
array_keys($arr); // Returns all the keys in an associative array.
array_values($arr); // Returns all the values in an associative array.
array_key_exists($arr); // Returns true if key is present in $arr.
array_unique($arr); // Returns only the unique values in an array.
array_diff($a, $b); // Returns only the non-unique elements between 2 arrays.
array_search('value', $arr); // Returns the index if the value is present else false.


// Manipulating Arrays
array_map('doubleNumber', $arr); // Apply the function 'doubleNumber' the $arr.
array_slice ($arr, $pos, $count); // Extract count number of elements starting from position pos in array arr.
array_reverse($arr); // Returns the reverse of array.


// Helper function
function doubleNumber(item) {
  return (item * 2);
}


// Creating Associative array
$asso_arr = array(
    "team" => "a",
    "brand" => "x",
    "members" => array(
        "mens" => array("Finn", "Seth", "Cody"),
        "womens" => array("Alexa", "Becky", "Mandy")
      )
  );

// Accessing Items in Multi-dimensional Associative array
echo $asso_arr['members']['mens'][2];

```

## Cookies

- Small piece of information which is stored at client browser.
- Usually used to recognize the user.
- Created at the server side and saved to client's browser.
- Cookie is created at server side and saved to client browser.
- Each time when client sends request to the server, cookie is embedded with request.
- General working of the cookies looks something like:

1. Make a request to the server.
2. Server returns the response and sends cookie along with it.
3. Subsequent requests from the client contains the cookie and sent to the server.

```php
// Creating Cookies
setCookie("name", "value", time() + 3600); // Set cookie with HTTP Response, and set to expire after 3600 seconds

// Using Cookies
echo $_COOKIE["name"]; // This will give you the access to the cookie's value.

// Deleting Cookies
setCookie("name", "value", time() - 3600); // Setting expiry in past will delete the cookie.

```

## Sessions

- Used to store and pass information from one page to another temporarily.
- Information is retained until the website is closed.
- Used commonly in e-com websites to store and pass information like product, cart or account info.
- Session creates unique user id for each browser to recognize the user and avoid conflict between multiple browsers.

```php
// Starting a new Session
session_start();

// Storing information in the Session.
$_SESSION['user'] = $username;

// Removing information from the session
unset($_SESSION['user']);

// Retrieving Information
echo $_SESSION['user'];

// Destroying Session.
session_destroy();

// Session Methods
session_id($id) // Get and/or set the current session id
session_unset() // Free all the session data.
session_name($name) // Get and/or set the current session name
session_status() // Returns the current status of the session.

```

## Functions

- In this example, `...$args` is an array of arguments.
- $args can contain any number of arguments

```php
function myFunction(...$args) {
  for ($args as $values) {
    // echo $values;
  }
}
```

## Math Functions

```php
abs($num); // Returns absolute value of a number
ceil($float); // Returns the next integer close to the decimal value.
floor($float); // Returns the previous integer close to the decimal value.
sqrt($num); // Returns the square root of the number
decbin($num); // Converts a number to binary
dechex($num); // Converts a number to hexadecimal
decoct($num); // Converts a number to octal
bindec($num); // Converts binary to decimal
base_convert($num, $fromBase, $toBase); // Converts a number to a specified base
```
