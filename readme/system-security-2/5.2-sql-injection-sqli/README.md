# 5.2 SQL Injection (SQLi)

## SQL Injection (SQLi)

**SQL Injection (SQLi)** is an attack method that exploits the injection of SQL commands into a web application's SQL queries. A successful SQLi attack allows a malicious hacker to access and manipulate the backend database of a web application.

Web applications, ranging from complex systems to Content Management Systems (CMSs) and simple personal web pages, often utilize databases like MySQL, SQL Server, Oracle, PostgreSQL, and others to store data, user credentials, or statistics. Structured Query Language (SQL) is employed by entities such as system operators, programmers, applications, and web applications to interact with databases.

SQL, a powerful interpreted language, is used to extract and manipulate data from databases. Web applications embed SQL commands, known as queries, in their server-side code, with connectors serving as middleware between the web application and the database.

Before delving into attack techniques, understanding some SQL basics is essential. This includes knowledge of SQL statement syntax, query execution, union operations, the DISTINCT and ALL operators, and how comments function.

Here below the three common types of SQL:

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

### SQL Statements

SQL allows the selection of constant values, such as:

```sql
SELECT 22, 'string', 0x12, 'another string';
```

Understanding the UNION command is crucial, as it performs a union between two results:

```sql
<SELECT statement> UNION <other SELECT statement>;
```

The DISTINCT operator eliminates duplicate rows, and a UNION statement implies DISTINCT by default. To allow duplicates, the ALL operator can be used:

```sql
<SELECT statement> UNION ALL <other SELECT statement>;
```

Comments in SQL can be denoted by either '#' or '-- '.

Example: The following queries showcase SQL operations on a database with two tables, "Products" and "Accounts."

```sql
SELECT Name, Description FROM Products WHERE ID='1';
SELECT Name, Description FROM Products WHERE Name='Shoes';
SELECT Name, Description FROM Products WHERE ID='3' UNION SELECT Username, Password FROM Accounts;
SELECT Name, Description FROM Products WHERE ID='3' UNION SELECT 'Example', 'Data';
```

### SQL Queries Inside Web Applications

In web applications, SQL queries are executed through the following steps:

1. Connect to the database.
2. Submit the query.
3. Retrieve and use the results in the application logic.

An example PHP code snippet demonstrates the process:

```php
$dbhostname = '1.2.3.4';
$dbuser = 'username';
$dbpassword = 'password';
$dbname = 'database';

$connection = mysqli_connect($dbhostname, $dbpassword, $dbname);
$query = "SELECT Name, Description FROM Products WHERE ID='3' UNION SELECT Username, Password FROM Accounts;";

$results = mysqli_query($connection, $query);
display_results($results);
```
