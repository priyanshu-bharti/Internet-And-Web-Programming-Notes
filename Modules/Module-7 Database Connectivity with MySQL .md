# Internet and Web Programming (ITA6003)

## Module 7 : Database Connectivity with MySQL

- [x] ~~MySQL Basics~~
- [x] ~~PHP DB Connectivity~~
- [x] ~~Querying MySQL Database~~

## MySQL Basics

```sql
/* Show all the databases */
SHOW DATABASES;

/* Create a new database */
CREATE DATABASE database_name;

/* Delete the database */
DROP DATABASE database_name;

/* Use a particular database */
USE database_name;

/* Create a new table */
CREATE TABLE tableName(
  id INT AUTO_INCREMENT,
  first_name VARCHAR(100),
  last_name VARCHAR(100),
  email VARCHAR(50),
  password VARCHAR(20),
  location VARCHAR(100),
  dept VARCHAR(100),
  is_admin TINYINT(1),
  register_date DATETIME,
  PRIMARY KEY(id)
);

/* Delete the table from the database */
DROP TABLE tablename;

/* Show Tables */
SHOW TABLES;

/* Describe the table's schema */
DESC tableName;

/* Insert Row */
INSERT INTO users
            (first_name,
             last_name,
             email,
             password,
             location,
             dept,
             is_admin,
             register_date)
VALUES      ('Brad',
             'Traversy',
             'brad@gmail.com',
             '123456',
             'Massachusetts',
             'development',
             1,
             Now());

/* Insert Multiple Rows */
INSERT INTO users
  (first_name,
    last_name,
    email,
    password,
    location,
    dept,
    is_admin,
    register_date)
VALUES  (
  'Fred',
  'Smith',
  'fred@gmail.com',
  '123456',
  'New York',
  'design',
  0,
  Now()),
 ('Sara',
  'Watson',
  'sara@gmail.com',
  '123456',
  'New York',
  'design',
  0,
  Now());

/* Select Statement */
SELECT * FROM users;
SELECT first_name, last_name FROM users;

/* Where Clause */
SELECT * FROM users WHERE location='Massachusetts';
SELECT * FROM users WHERE location='Massachusetts' AND dept='sales';
SELECT * FROM users WHERE is_admin = 1;
SELECT * FROM users WHERE is_admin > 0;

/* Delete Row */
DELETE FROM users WHERE id = 6;

/* Update Row */
UPDATE users SET email = 'freddy@gmail.com' WHERE id = 2;

/* Add new column */
ALTER TABLE users ADD age VARCHAR(3);

/* Modify Column */
ALTER TABLE users MODIFY COLUMN age INT(3);

/* Order By */
SELECT * FROM users ORDER BY last_name ASC;
SELECT * FROM users ORDER BY last_name DESC;

/* Select Distinct Rows */
SELECT DISTINCT location FROM users;

/* Select the data between 2 values */
SELECT * FROM users WHERE age BETWEEN 20 AND 25;

/* Inner join */
SELECT
  users.first_name,
  users.last_name,
  posts.title,
  posts.publish_date
FROM users
INNER JOIN posts
ON users.id = posts.user_id
ORDER BY posts.title;
```

## PHP DB Connectivity

### Inserting data in the table

**HTML Form**

```html
<form action="connect.php" method="POST">
  Enter Name : <input type="text" name="name" id="name" /> Enter Email :
  <input type="email" name="email" id="email" /> Enter Password :
  <input type="password" name="password" id="password" />
  <input type="submit" value="Submit" />
</form>
```

**PHP Code**

```php
<?php

// Connection Details
$hostname = "localhost";
$username = "root";
$password = "";
$db_name = "test";

// Create a new connection
$connection = mysqli_connect($hostname, $username, $password, $db_name);

// Get the information from the form and store it
$name = $_POST['name'];
$email = $_POST['email'];
$password = $_POST['password'];

// Insert the information to the table in the database
$query = "INSERT INTO `reg` (`name`, `email`, `password`) VALUES ('$name', '$email', '$password')";

// Execute the query
$res = mysqli_query($connection, $query);

// Display some information
echo $res? "Success" : "Error";

?>
```

### Display the information from the database

**PHP Code**

```php
<?php
// Connection Details
$hostname = "localhost";
$username = "root";
$password = "";
$db_name = "test";

// Create a new connection
$connection = mysqli_connect($hostname, $username, $password, $db_name);

// Insert the information to the table in the database
$query = "SELECT * FROM `reg`";

// Execute the query
$res = mysqli_query($connection, $query);

// Get a row of table
$res = $res->fetch_assoc();

// Display the information
echo "<br>name : " . $res["name"] . "<br>email : " . $res["email"] . "<br>password : " . $res["password"];
?>
```

## Login and Signup using PHP

### connection.php

```php
<?php

// Connection Details
$hostname = 'localhost';
$username = 'root';
$password = '';
$database = 'test';

// Make a connection
$conn = mysqli_connect($hostname, $username, $password, $database);

?>
```

### register.html

```html
<html lang="en">
  <head>
    <title>Register</title>
  </head>

  <body>
    <form action="register.php" method="POST">
      Name: <input required type="text" name="name" id="name" /> <br /><br />
      Email: <input required type="email" name="email" id="email" />
      <br /><br />
      Password:
      <input required type="password" name="password" id="password" />
      <br /><br />
      Re-enter Password:
      <input required type="password" name="repass" id="repass" /> <br /><br />
      <input type="submit" name="submit" value="Register" />
    </form>
  </body>
</html>
```

### register.php

```php
<?php

// Import the connection
require "connection.php";

// Get the information from the user
if (isset($_POST['submit'])) {
  $name = $_POST['name'];
  $email = $_POST['email'];
  $pass = $_POST['pass'];

  // Check if the user is already registered
  $query = "SELECT * FROM `test` WHERE `email` = '$email'"; // Prepare the query
  $res = mysqli_query($conn, $query); // Execute the query

  // Check if no rows are returned
  if ($res->num_rows == 0) {
    // Add the user to the database
    $query = "INSERT INTO `test` (`name`, `email`, `password`) VALUES ('$name', '$email', '$pass')";
    // Execute the query
    $res = mysqli_query($conn, $query);

    if ($res) {
      echo "Successfully Registered";
    } else {
      echo "Error Occurred";
    }
  } else {
    echo "This email already exists";
  }

  // Log in the user
  // Start the session
  session_start();
  // Set the login session as user's name
  $_SESSION['login'] = $name;
  // Redirect
  header("Location: ./home.php");
}
?>
```

### login.html

```html
<html lang="en">
  <head>
    <title>Login</title>
  </head>
  <body>
    <form action="login.php" method="POST">
      Email: <input required type="email" name="email" id="email" />
      <br /><br />
      Password:
      <input required type="password" name="password" id="password" />
      <br /><br />
      <input type="submit" name="submit" value="Login" />
    </form>
  </body>
</html>
```

### login.php

```php
<?php

// Create the connection
require "connection.php";

// Get the credentials from the user
if (isset($_POST['submit'])) {
  $email = $_POST['email'];
  $pass = $_POST['pass'];

  // Match the credentials and retrieve the name
  $query = "SELECT `name` FROM `test` WHERE `email` = '$email' AND `pass` = '$pass'";

  // Execute the query
  $res = mysqli_query($conn, $query);

  // Check if no users are found
  if ($res->num_rows == 0) {
    echo "<script>alert('Invalid Credentials')</script>";
  } else {
    // Get the name of the user from the rows returned.
    $name = $res->fetch_assoc['name'];
    
    // Log in the user if no one is logged in.
    if (!isset($_SESSION['login'])) {
      // Start the session
      session_start();
      // Set the login session as user's name
      $_SESSION['login'] = $name;
      // Redirect
      header("Location: ./home.php");
    }
  }
} else {
  echo "Please login first";
}
?>
```

### home.PHP

```php
<html lang="en">
<head>
  <title>Document</title>
</head>
<body>
  <?php
  session_start();
  echo $_SESSION['login'];
  ?>

  <br>
  
  <form action="home.php" method="POST">
    <input type="submit" value="Logout" name="logout">
  </form>

  <?php
  // Check if the user has pressed the logout button
  if (isset($_POST['logout'])) {
    // Show an alert
    echo "<script>alert('Successfully Logged Out!')</script>";
    // Remove the login information
    unset($_SESSION['login']);
    // Destroy the session
    session_destroy();
    header('Location: ./login.html');
  }
  ?>
</body>
</html>

```