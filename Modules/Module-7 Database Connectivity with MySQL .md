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
