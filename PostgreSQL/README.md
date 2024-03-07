# What is PostgreSQL ?
PostgreSQL is a powerful open-source relational database management system (RDBMS) known for its reliability, robust feature set, and adherence to SQL standards. Originally developed at the University of California, Berkeley, PostgreSQL has a long history dating back to the mid-1980s.

**Key features of PostgreSQL include:**

- ACID Compliance: PostgreSQL ensures that all transactions are processed in a manner that maintains the ACID (Atomicity, Consistency, Isolation, Durability) properties, ensuring data integrity.

- Extensibility: PostgreSQL offers a rich set of built-in data types, functions, and extensions, allowing users to customize and extend the functionality of the database system according to their specific needs.

- Support for JSON and JSONB data types: PostgreSQL provides native support for JSON (JavaScript Object Notation) data, allowing users to store and query JSON documents efficiently. The JSONB data type offers additional capabilities for indexing and querying JSON data.

- Advanced Indexing: PostgreSQL supports various types of indexes, including B-tree, Hash, GiST (Generalized Search Tree), GIN (Generalized Inverted Index), and BRIN (Block Range Index). These indexes enable efficient data retrieval and query optimization.

- Full-text Search: PostgreSQL includes robust full-text search capabilities, allowing users to perform complex text searches on large volumes of textual data.

- Foreign Data Wrappers (FDW): PostgreSQL supports Foreign Data Wrappers, which enable users to access and manipulate data stored in external data sources (such as other databases or web services) as if it were part of the PostgreSQL database.

- Replication and High Availability: PostgreSQL supports various replication methods, including streaming replication, logical replication, and synchronous replication, to ensure high availability and fault tolerance.

- Security Features: PostgreSQL provides robust security features, including role-based access control (RBAC), SSL encryption, and support for secure authentication mechanisms such as LDAP and Kerberos.

- Scalability: PostgreSQL is designed to scale efficiently, supporting large databases and high-volume transactional workloads. It can be deployed on a single server or in a distributed architecture using tools like PostgreSQL's native partitioning and sharding capabilities or external solutions like Citus Data.

# What is pgAdmin ?

pgAdmin is a popular open-source graphical user interface (GUI) administration tool for managing PostgreSQL databases. It provides users with a convenient way to interact with PostgreSQL databases through a visual interface, making tasks such as database creation, querying, administration, and monitoring more accessible, especially for users who may not be comfortable with command-line interfaces.

# SELECT Query

A SELECT query is one of the most fundamental operations in SQL (Structured Query Language) used to retrieve data from a database table or multiple tables. The basic syntax of a SELECT query is as follows:

```sql
SELECT column1, column2, ...
FROM table_name;
```

Where:

SELECT is the keyword used to indicate that you want to retrieve data.
column1, column2, ... are the columns you want to retrieve from the table. You can specify one or more columns, or you can use * to select all columns.
table_name is the name of the table from which you want to retrieve data.
For example, suppose you have a table named employees with columns employee_id, first_name, last_name, and salary. To retrieve the first_name and last_name of all employees from the employees table, you can write the following SELECT query:

```sql
SELECT first_name, last_name
FROM employees;
```

If you want to retrieve all columns from the employees table, you can use the wildcard *:

```sql
SELECT *
FROM employees;
```

You can also include additional clauses in the SELECT query to filter or sort the retrieved data, such as WHERE for filtering rows based on specific conditions, ORDER BY for sorting the result set, GROUP BY for grouping rows based on specific columns, and HAVING for filtering grouped rows.

Here's an example of a SELECT query with a WHERE clause to retrieve employees with a salary greater than 50000:

```sql
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE salary > 50000;
```
This query retrieves the employee_id, first_name, last_name, and salary of employees from the employees table where the salary is greater than 50000.

# DISTINCT Query

A DISTINCT query in SQL is used to retrieve unique values from a specific column or combination of columns in a table. It removes duplicate rows from the result set, ensuring that each row returned by the query contains unique values.

The basic syntax of a SELECT query with DISTINCT is as follows:

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
Where:

SELECT DISTINCT is the keyword combination indicating that you want to retrieve unique values.
column1, column2, ... are the columns from which you want to retrieve unique values. You can specify one or more columns.

For example, suppose you have a table named orders with a column named product_id that contains duplicate entries. To retrieve the unique product IDs from the orders table, you can use the following query:

```sql
SELECT DISTINCT product_id
```
FROM orders;
This query will return only distinct values of product_id from the orders table, removing any duplicate entries.

You can also use the DISTINCT keyword with multiple columns to retrieve unique combinations of values across those columns. For example:

```sql
SELECT DISTINCT column1, column2
FROM table_name;
```
This query will return unique combinations of values from column1 and column2 in the result set, removing duplicate combinations.

It's important to note that using DISTINCT can affect the performance of the query, especially on large datasets, as the database engine needs to perform additional processing to identify and remove duplicate rows.

# COUNT 

The COUNT function in SQL is used to count the number of rows that match a specified condition within a table or result set. It is commonly used to determine the number of records in a table or to calculate the number of rows that meet certain criteria.

The basic syntax of the COUNT function is as follows:

```sql
SELECT COUNT(*)
FROM table_name;
```
This query will return the total number of rows in the specified table.

You can also use the COUNT function with a specific column to count the number of non-null values in that column:

```sql
SELECT COUNT(column_name)
FROM table_name;
```

This query will count the number of non-null values in the specified column of the table.

Additionally, you can use the COUNT function with a WHERE clause to count the number of rows that meet specific conditions:

```sql
SELECT COUNT(*)
FROM table_name
```
WHERE condition;

For example, if you have a table named employees and you want to count the number of employees with a salary greater than 50000, you can use the following query:

```sql
SELECT COUNT(*)
FROM employees
WHERE salary > 50000;
```

The COUNT function can also be combined with other SQL functions and clauses, such as DISTINCT, GROUP BY, HAVING, and JOIN, to perform more complex calculations and analysis on the data.

It's important to note that the COUNT function always returns an integer value representing the number of rows that match the specified condition. If there are no matching rows, COUNT will return 0.

# WHERE CLAUSE
 "where" clause is used to specify a condition while retrieving data from a database. It allows you to filter records based on specified criteria. Here's a basic example:

```sql
SELECT column1, column2
FROM table_name
```
WHERE condition;
In this syntax:

"SELECT" specifies the columns you want to retrieve.
"FROM" specifies the table you're retrieving data from.
"WHERE" specifies the condition that must be met for a record to be included in the result set.
For instance, if you have a table called "employees" and you want to retrieve the names of all employees who are in the sales department, you would use a query like this:

```sql
SELECT name
FROM employees
WHERE department = 'Sales';
```
This query will return the names of all employees where the department column equals 'Sales'. The "where" clause allows you to narrow down your results to only include records that meet specific criteria.


**Equality: Check if a column is equal to a specific value.**

```sql
WHERE column_name = value
```
**Inequality: Check if a column is not equal to a specific value.**

```sql
WHERE column_name <> value
```
**Range: Check if a column's value falls within a range.**

```sql
WHERE column_name BETWEEN value1 AND value2
```
**NULL: Check if a column is NULL.**

```sql
WHERE column_name IS NULL
```
**NOT NULL: Check if a column is not NULL.**

```sql
WHERE column_name IS NOT NULL
```
**Pattern Matching: Use wildcards to search for patterns in string values.**

```sql
WHERE column_name LIKE 'pattern'
```
**Logical Operators: Use logical operators (AND, OR, NOT) to combine conditions.**

```sql
WHERE condition1 AND condition2
WHERE condition1 OR condition2
WHERE NOT condition
```
**IN: Check if a column's value is within a list of specified values.**

```sql
WHERE column_name IN (value1, value2, ...)
```
**NOT IN: Check if a column's value is not within a list of specified values.**

```sql
WHERE column_name NOT IN (value1, value2, ...)
```

# ORDERBY CLAUSE

The ORDER BY clause in SQL is used to sort the result set of a query based on one or more columns. It allows you to control the order in which the rows are returned by specifying the columns by which you want to sort and the sort direction (ascending or descending).

The basic syntax of the ORDER BY clause is as follows:

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ...;
```
Where:

SELECT column1, column2, ... specifies the columns you want to retrieve in the result set.
FROM table_name specifies the table from which you want to retrieve the data.  

ORDER BY column1 [ASC | DESC], column2 [ASC | DESC], ... specifies the columns by which you want to sort the result set. You can specify one or more columns separated by commas. By default, the sort order is ascending (ASC), but you can explicitly specify descending (DESC) if you want to sort in descending order.
For example, suppose you have a table named employees with columns employee_id, first_name, and last_name, and you want to retrieve the employees sorted by their last names in ascending order. You can use the following query:

```sql
SELECT employee_id, first_name, last_name
FROM employees
ORDER BY last_name ASC;
```
If you want to sort the employees by their last names in descending order, you can specify DESC after the column name:

```sql
SELECT employee_id, first_name, last_name
FROM employees
ORDER BY last_name DESC;
```
You can also sort the result set by multiple columns. For example, to sort the employees by their last names in ascending order and then by their first names in descending order, you can use:

```sql
SELECT employee_id, first_name, last_name
FROM employees
ORDER BY last_name ASC, first_name DESC;
```
The ORDER BY clause is commonly used to organize query results in a meaningful way, making it easier to analyze and interpret the data.

# LIMIT CLAUSE

The LIMIT clause in SQL is used to restrict the number of rows returned by a query. It is particularly useful when dealing with large result sets, as it allows you to retrieve only a specified number of rows from the beginning of the result set.

The basic syntax of the LIMIT clause is as follows:

```sql
SELECT column1, column2, ...
FROM table_name
LIMIT number_of_rows;
```
Where:

SELECT column1, column2, ... specifies the columns you want to retrieve in the result set.
FROM table_name specifies the table from which you want to retrieve the data.
LIMIT number_of_rows specifies the maximum number of rows to return in the result set.
For example, if you want to retrieve the first 10 rows from a table named employees, you can use the following query:

```sql
SELECT *
FROM employees
LIMIT 10;
```
You can also use the LIMIT clause in combination with the ORDER BY clause to retrieve a specified number of rows and sort them according to a specific column or columns. For example, to retrieve the first 10 employees sorted by their last names in ascending order, you can use:

```sql
SELECT *
FROM employees
ORDER BY last_name ASC
LIMIT 10;
```
Additionally, you can use OFFSET along with LIMIT to skip a certain number of rows before returning the result set. This is useful for implementing pagination in applications. For example, to retrieve the next 10 employees after skipping the first 10, you can use:

```sql
SELECT *
FROM employees
ORDER BY last_name ASC
LIMIT 10 OFFSET 10;
```
This query will retrieve rows 11 to 20 from the employees table, sorted by last name in ascending order.

The LIMIT clause is supported by most relational database management systems, including PostgreSQL, MySQL, SQLite, and others. However, the syntax for limiting rows may vary slightly between different database systems.

# BETWEEN CLAUSE
The BETWEEN clause in SQL is used to select values within a specified range. It allows you to specify a range of values for a column and retrieve rows where the column value falls within that range. The BETWEEN clause is inclusive, meaning it includes the start and end values of the range.

The basic syntax of the BETWEEN clause is as follows:

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name BETWEEN value1 AND value2;
```
Where:

SELECT column1, column2, ... specifies the columns you want to retrieve in the result set.
FROM table_name specifies the table from which you want to retrieve the data.
WHERE column_name BETWEEN value1 AND value2 specifies the column name and the range of values you want to filter on.
For example, suppose you have a table named employees with a column named salary, and you want to retrieve employees with salaries between $50,000 and $70,000. You can use the following query:

```sql
SELECT *
FROM employees
WHERE salary BETWEEN 50000 AND 70000;
```
This query will retrieve all rows from the employees table where the salary column value falls between $50,000 and $70,000, inclusive.

You can also use the BETWEEN clause with dates, strings, or any other comparable data types. For example, to retrieve orders placed between two specific dates, you can use:

```sql
SELECT *
FROM orders
WHERE order_date BETWEEN '2023-01-01' AND '2023-12-31';
```
This query will retrieve all rows from the orders table where the order_date falls between January 1, 2023, and December 31, 2023, inclusive.

Keep in mind that the BETWEEN clause is inclusive, so rows with values equal to value1 or value2 are included in the result set. If you want to exclude the endpoints, you may need to use other comparison operators (such as < and >) combined with the AND operator.

# IN CLAUSE
The IN clause in SQL is used to specify multiple values for a column and retrieve rows where the column value matches any of those specified values. It allows you to simplify queries where you want to filter rows based on a list of specific values.

The basic syntax of the IN clause is as follows:

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column_name IN (value1, value2, ...);
```
Where:

SELECT column1, column2, ... specifies the columns you want to retrieve in the result set.
FROM table_name specifies the table from which you want to retrieve the data.
WHERE column_name IN (value1, value2, ...) specifies the column name and the list of values you want to filter on.
For example, suppose you have a table named employees with a column named department and you want to retrieve employees who work in either the 'HR' or 'Finance' departments. You can use the following query:

```sql
SELECT *
FROM employees
WHERE department IN ('HR', 'Finance');
```
This query will retrieve all rows from the employees table where the department column value matches either 'HR' or 'Finance'.

You can specify any number of values within the parentheses after the IN keyword. These values can be literals, variables, or subqueries.

The IN clause can also be combined with other conditions using logical operators such as AND and OR. For example, you can retrieve employees who work in the 'HR' department and have a salary greater than $50,000 using:

```sql
SELECT *
FROM employees
WHERE department = 'HR' AND salary > 50000;
```
Or you can retrieve employees who work in either the 'HR' or 'Finance' departments and have a salary greater than $50,000 using:

```sql
SELECT *
FROM employees
WHERE (department = 'HR' OR department = 'Finance') AND salary > 50000;
```
Using the IN clause can make your queries more concise and readable, especially when dealing with multiple values or complex conditions.

# EXTRACT

In SQL, the EXTRACT function is used to extract parts of a date or time value, such as the year, month, day, hour, minute, etc. It allows you to retrieve specific components of a date or time value, which can be useful for performing calculations, comparisons, or formatting operations.

The basic syntax of the EXTRACT function is as follows:

```sql
EXTRACT(field FROM source)
```
Where:

field specifies the part of the date or time value you want to extract (e.g., 'year', 'month', 'day', 'hour', 'minute', 'second').
source is the date or time value from which you want to extract the specified part.
For example, if you have a table named orders with a column named order_date containing date values, you can use the EXTRACT function to retrieve the year, month, and day components of the order_date:

```sql
SELECT EXTRACT(YEAR FROM order_date) AS order_year,
       EXTRACT(MONTH FROM order_date) AS order_month,
       EXTRACT(DAY FROM order_date) AS order_day
FROM orders;
```
This query will extract the year, month, and day components from the order_date column for each row in the orders table.

You can also use the EXTRACT function with other date or time components such as 'hour', 'minute', 'second', 'timezone_hour', 'timezone_minute', etc., depending on your requirements.

It's important to note that the availability of date and time components may vary depending on the SQL database system you're using. Additionally, the EXTRACT function may have different syntax or behavior in different SQL database systems, so always refer to the documentation specific to your database system for accurate usage details.

<details>
<summary><b>More about EXTRACT: </b></summary>
EXTRACT function in combination with the WHERE clause to filter rows based on specific date or time components. For example, if you want to retrieve orders that were placed in a specific month, you can use the EXTRACT function to extract the month component from the order date and then filter based on that value. Here's an example:

```sql
SELECT *
FROM orders
WHERE EXTRACT(MONTH FROM order_date) = 3; -- Retrieves orders placed in March
```
In this query, EXTRACT(MONTH FROM order_date) extracts the month component from the order_date column for each row, and then the WHERE clause filters the result set to include only rows where the extracted month is equal to 3 (March).

Similarly, you can use EXTRACT with other date or time components and combine it with WHERE to filter based on specific criteria. For example, to retrieve orders placed in the year 2023:

```sql
SELECT *
FROM orders
WHERE EXTRACT(YEAR FROM order_date) = 2023;
```
Or to retrieve orders placed on a specific day of the week (e.g., Monday):

```sql
SELECT *
FROM orders
WHERE EXTRACT(DOW FROM order_date) = 1; -- 1 represents Monday
```

In this query, EXTRACT(DOW FROM order_date) extracts the day of the week component (where Sunday is 0 and Monday is 1) from the order_date column for each row, and then the WHERE clause filters the result set to include only rows where the extracted day of the week is equal to 1 (Monday).
</details>

# AGGREGATE Function

Aggregate functions in SQL are functions that operate on sets of rows and return a single value as a result. These functions allow you to perform calculations across multiple rows of a table and are commonly used for tasks such as summarizing data, calculating averages, finding maximum or minimum values, and counting the number of rows that meet certain criteria.

Some of the most commonly used aggregate functions in SQL include:

COUNT: Returns the number of rows that match a specified condition.

```sql
SELECT COUNT(*) FROM table_name; -- Count all rows in the table
SELECT COUNT(column_name) FROM table_name WHERE 
condition; -- Count rows that meet a condition
```
SUM: Calculates the sum of values in a numeric column.

```sql
SELECT SUM(column_name) FROM table_name;
```
AVG: Calculates the average value of a numeric column.

```sql
SELECT AVG(column_name) FROM table_name;
```
MAX: Returns the maximum value in a column.

```sql
SELECT MAX(column_name) FROM table_name;
```
MIN: Returns the minimum value in a column.

```sql
SELECT MIN(column_name) FROM table_name;
```
GROUP_CONCAT (specific to some databases like MySQL): Concatenates values from multiple rows into a single string.

```sql
SELECT GROUP_CONCAT(column_name) FROM table_name;
```
GROUP BY: Groups the result set by one or more columns and allows you to perform aggregate functions on each group separately.

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1;
```
HAVING: Filters groups based on aggregate values calculated using GROUP BY.

```sql
SELECT column1, aggregate_function(column2)
FROM table_name
GROUP BY column1
HAVING aggregate_function(column2) > value;
```
These aggregate functions are powerful tools for summarizing and analyzing data in SQL. They allow you to derive useful insights and metrics from large datasets efficiently.

# ROUND Function
The ROUND function in SQL is used to round a numeric value to a specified number of decimal places. It takes two arguments: the numeric value to be rounded and the number of decimal places to round to.

The basic syntax of the ROUND function is as follows:

```sql
ROUND(numeric_expression, decimal_places)
```
Where:

numeric_expression is the numeric value you want to round.
decimal_places is the number of decimal places to which you want to round the numeric value.
For example, if you have a numeric column named price in a table named products, and you want to round the prices to two decimal places, you can use the ROUND function like this:

```sql
SELECT ROUND(price, 2) AS rounded_price
FROM products;
```
This query will round the price column values to two decimal places and display the rounded values as rounded_price.

You can also use negative values for decimal_places to round to the nearest multiple of 10, 100, etc. For example, if you want to round to the nearest hundred, you can use:

```sql
SELECT ROUND(price, -2) AS rounded_price
FROM products;
```
This query will round the price column values to the nearest hundred.

Additionally, if decimal_places is omitted, the ROUND function will round to the nearest integer. For example:

```sql
SELECT ROUND(price) AS rounded_price
FROM products;
```
This query will round the price column values to the nearest integer.













