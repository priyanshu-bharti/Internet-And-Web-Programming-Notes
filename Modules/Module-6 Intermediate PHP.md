# Internet and Web Programming (ITA6003)

## Module 6 : Intermediate PHP

- [x] ~~Form Handling~~
- [x] ~~Include and Require~~
- [x] ~~File Handling~~
- [x] ~~File Uploading~~
- [x] ~~File Downloading~~
- [x] ~~Working with Date and Time~~
- [x] ~~Email without attachment~~
- [x] ~~Email with attachment~~
- [x] ~~Working With Date and Time~~

## Form Handling

- Once the form has been submitted, we can get the data using the `$_GET` and `$_POST`.
- If we use `GET` method, variable names and values are displayed in the URL.
- Since the values are appended in the URL, it is possible to be bookmarked.
- `GET` method values can't exceed more than 100 characters.
- Information sent from a form with the POST method is invisible to others and has no limits on the amount of information to send.
- 8 Mb max size for the POST method, by default.

### HTML Form

```html
<form action="test.php" method="POST">
  Email : <input type="email" name="email" id="email" /> <br />
  Password : <input type="password" name="password" id="password" /> <br />
  <input type="submit" value="Submit" />
</form>
```

### PHP File

```php
<?php
  echo "Email : " . $_POST['email'] . "<br/>";
  echo "Password : " . $_POST['password'] . "<br/>";
?>
```

## Include and Require

- We can create reusable components which can be called in PHP.
- Initially, it might take time to refactor such components, but in the long run, it saves time.
- Both `include` and `require` are similar in working, however they both handle failure differently.
- The advantages that it brings are : code reuse, and editablility.
- `include` only generates a warning, i.e., E_WARNING, and continue the execution of the script.
- `require` generates a fatal error, i.e., E_COMPILE_ERROR, and stop the execution of the script.

### Component (menu.html)

```html
<nav>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>
```

### PHP application

```php
<?php
include "menu.html"; // OR
require "menu.html";
?>
```

## File Handling

- File handling is needed for any application.
- For some tasks to be done, file needs to be processed.
- PHP has many functions to work with normal files. Those functions are:

1. `fopen()` : PHP `fopen($location, $mode)` function is used to open a file.
2. `filesize()` : Allows us to calculate the size of file `filesize($location)`.
3. `fread()` : We can read file contents using `fread($file, $size)` after the file is opened.
4. `fgets()` : Read the content line by line using `fgets($file)` after the file is opened.
5. `fgetc()` : Read the content character by character using `fgetc($file)` after the file is opened.
6. `readfile()` : Open a file and read all its contents `readfile($file)`.
7. `fwrite()` : We can write to the file using `fwrite($file, $text)`.
8. `fclose()` : It is important to close the file after we're done with it using `fclose($file)`.
9. `unlink()` : We can delete the file using `unlink($location)`.

### File Opening Modes:

- `w` : Open in Write only, clears existing data (Creates new file if doesn't exist).
- `r` : Open in Read only.
- `a` : Open in Write only, Appends new contents after existing data.
- `w+` : Opens in Read and Write. clears existing data (Creates new file if doesn't exist).
- `r+` : Opens in Read and Write.
- `a+` : Open in Read and Write, Appends new contents after existing data.
- `x` : Create new file and Open in Write only.

### Basic File Read Operation

```php
<?php
// File Details
$location = "file.txt";


// Opening File in Append
$mode = "a";
$file = fopen($location, $mode) or die("Can't open file");


// Append Content
$text = "\nMERN = Mongo Express Node React Stack";
fwrite($file, $text);


// Close File
fclose($file);


// Opening File in Read Only
$mode = "r";
$file = fopen($location, $mode) or die("Can't open file");


// Read the contents and output a line of file at a time.
while(!feof($file)) {
  echo fgets($file) . "<br>"; // OR echo fgetc($file); for char by char mode.
}


// Read the contents and output a single line
echo fread($file, $size)


// Readfile is same as the above statement
echo readfile($location);


// Close File
fclose($file);
?>
```

## File Uploading

- `$_FILES` contains all the information of file.
- We can get file name, file type, file size, temp file name and errors associated with file.
- We can use the following methods below.

```php
$_FILES['filename']['name'] // File name.
$_FILES['filename']['type'] // MIME type of the file.
$_FILES['filename']['size'] // Size of the file (in bytes).
$_FILES['filename']['tmp_name'] // Temp. name of the file stored on the server.
$_FILES['filename']['error'] // Error associated with the file.
```

- There is also a method called `move_uploaded_file()` which can be used to move the uploaded file to a different location on the server.

### Basic Upload Program

**HTML File**

```html
<form action="test.php" method="POST" enctype="multipart/form-data">
  <input type="file" name="uploadedFile" />
  <input type="submit" value="Submit" />
</form>
```

**PHP File**

```php
<?php
  // File Details
  $uploaded_file = $_FILES['uploadedFile'];


  // Path
  $destination = "./";
  $destination = $destination.$uploaded_file['name'];


  // Move the uploaded file in the destination folder
  if (move_uploaded_file($uploaded_file['tmp_name'], $destination)) {
    echo "Uploaded file successfully";
  } else {
    echo "File Upload Failed!";
  }
?>
```

## File Downloading

- We need to provide the url to the file, which can be either local or hostel on the internet.
- Then we need to provide 3 headers:

1. `Content-Type` : it is going to be `application/octet-stream` for every type of file.
2. `Content-Transfer-Encoding` : it is going to be `utf-8` for text based files or `binary` for executable files.
3. `Content-disposition: attachment; filename="$url"` : You have to specify the url here to download the file.

```php
<?php
  // URL Details
  $url = "https://raw.githubusercontent.com/priyanshu-bharti/priyanshu-bharti/main/README.md";


  // Setting up the headers
  header('Content-Type: application/octet-stream');
  header('Content-Transfer-Encoding: utf-8');
  header(`Content-disposition: attachment; filename="$url"`);


  // Reading the file to start downloading.
  readFile($url);
?>
```

## Email without attachment

```php
<?php
// Email Details
$receiver = "receiver@gmail.com";
$subject = "Subject";
$message = "<p>This is a message</p>";

// Header Details
$header = "From: priyanshub25@gmail.com ";
$header.= "MIME-Version: 1.0 ";
$header.= "Content-type: text/html;charset=UTF-8 ";

// Result
$result = mail($receiver, $subject, $message, $header);

// Display the message
if($result) {
  echo "Mail Sent Successfully!";
} else {
  echo "Error Sending Mail!";
}
?>
```

## Email with attachment

```php
// Email Details
$receiver = "receiver@gmail.com";
$subject = "Subject";
$message = "<p>This is a message</p>";

// Open a file attachment
$file = fopen("attachment.txt", "r") or die("Could not open file");
$content = readfile("attachment.txt");

// Encode the contents of the file
$encoded_content = chunk_split(base64_encode($content));

// Main Header Details
$header = "From: priyanshub25@gmail.com ";
$header.= "MIME-Version: 1.0 ";
$header.= "Content-type: multipart/mixed ";

// Message Headers
$header.= 'Content-Type: text/html';
$header.= 'Content-Transfer-Encoding: utf-8';
$header.= $message;

// Attachment Headers
$header.= 'Content-Type: application/octet-stream';
$header.= 'Content-Transfer-Encoding: base64';
$header.= 'Content-disposition: attachment; filename="attachment.txt"';
$header.= $encoded_content;

// Send Mail
$result = mail($to, $subject, "", $header);

// Display the message
if($result) {
  echo "Mail Sent Successfully!";
} else {
  echo "Error Sending Mail!";
}
```

## Working with Date and Time

### Time Format Strings

- `H` : Hours in 2 digit 24 hours format.
- `h` : Hours in 2 digit 12 hours format.
- `i` : Minutes
- `s` : Seconds
- `a` : AM / PM in lowercase
- `A` : AM / PM in Uppercase

### Day Format Strings

- `d` : Day of the month
- `D` : Mon, Tue, ... in 3 letters
- `m` : Months in 2 digits (01 - 12)
- `y` : Year in 2 digits
- `Y` : Year in 4 digits

```php
echo date("h:i:s a"); // 03:45:32 pm
echo date("d/m/Y"); // 01/06/1999
echo date("F, l the jS, Y"); // November, Friday the 13th, 2022
```

### Creating Date and Time

```php
// Create a date using mktime()
mktime(hour, minute, second, month, day, year);

// Get an object
$d=mktime(11, 14, 54, 8, 12, 2014); // 11:14:54(am) 12/08/2014

// Creating date object using strings
$d=strtotime("10:30pm April 15 2014"); // Same format as the mktime parameters.
$d=strtotime("tomorrow");
$d=strtotime("next Saturday");
$d=strtotime("+3 Months");

// Counting the number of days left till we reach a certain date.
$certain_date = "1 June";
$d1=strtotime($certain_date);
$d2=ceil(($d1-time())/60/60/24);
echo "There are " . $d2 ." days until ". $certain_date;

```