# 5.8 Blind SQLi

## Exploiting Blind SQL Injection

Blind SQL injection is an inference methodology used to extract database schemas and data when direct in-band or error-based SQL injections are not possible. This technique relies on transforming a query into a True/False condition and observing the application's response.

#### **Exploitation Scenario**

* **Identifying Dynamic Query Structure:** Assuming the query structure is like: `SELECT <fields> FROM <table> WHERE id='<id parameter>';`, you can attempt to trigger always true and always false conditions. For example, `' OR 'a'='a` and `' OR '1'='11`. If the application responds differently for true and false conditions, it indicates a potential blind SQL injection.

### **Detecting the Current User**

* **Using MySQL Functions:** By employing MySQL functions like `user()` and `substring()`, you can iteratively guess the characters of the current database user's username. For example:
  * `' or substr(user(), 1, 1) = 'a`
  * `' or substr(user(), 1, 1) = 'b`
  * Continue this process until the full username is identified.

### **Scripting Blind SQLi Data Dump**

* **Automation with SQLMap:** SQLMap is a tool that automates the process of detecting and exploiting SQL injection vulnerabilities, including blind SQL injections. It can significantly simplify the process of dumping data from a database.
* **Optimizing Payloads:** To speed up the exploitation, it's crucial to narrow down the charset by optimizing payloads. By testing if the conversion to upper or lower case of a character yields a true or false condition, you can determine if the character is uppercase, lowercase, or a number/symbol.

### **Time-Based Blind SQL Injection**

* **Time-Based Technique:** Time-based blind SQL injection involves inferring a true condition from a false condition based on the delay in the application's response. For example:
  * `IF (SELECT user) = 'sa' WAITFOR DELAY '0:0:5'`
* **Example with MySQL:**
  * `IF EXISTS (SELECT * FROM users WHERE username = 'armando') BENCHMARK(1000000, MD5(1))`
  * This query performs the MD5 function 1,000,000 times if the condition is true.
* **Caution with BENCHMARK():** Be cautious with the first argument of BENCHMARK(), as it can significantly affect server load.

Blind SQL injection, whether time-based or boolean-based, requires a systematic approach to iteratively guess and extract information from the database. Automation tools like SQLMap can be invaluable in efficiently exploiting blind SQL injection vulnerabilities. Always exercise caution to avoid unintended consequences, especially when using delay functions like `BENCHMARK()` in time-based injections.
