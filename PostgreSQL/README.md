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
Copy code
SELECT column1, column2, ...
FROM table_name;
```

Where:

SELECT is the keyword used to indicate that you want to retrieve data.
column1, column2, ... are the columns you want to retrieve from the table. You can specify one or more columns, or you can use * to select all columns.
table_name is the name of the table from which you want to retrieve data.
For example, suppose you have a table named employees with columns employee_id, first_name, last_name, and salary. To retrieve the first_name and last_name of all employees from the employees table, you can write the following SELECT query:

```sql
Copy code
SELECT first_name, last_name
FROM employees;
```

If you want to retrieve all columns from the employees table, you can use the wildcard *:

```sql
Copy code
SELECT *
FROM employees;
```

You can also include additional clauses in the SELECT query to filter or sort the retrieved data, such as WHERE for filtering rows based on specific conditions, ORDER BY for sorting the result set, GROUP BY for grouping rows based on specific columns, and HAVING for filtering grouped rows.

Here's an example of a SELECT query with a WHERE clause to retrieve employees with a salary greater than 50000:

```sql
Copy code
SELECT employee_id, first_name, last_name, salary
FROM employees
WHERE salary > 50000;
```
This query retrieves the employee_id, first_name, last_name, and salary of employees from the employees table where the salary is greater than 50000.

# DISTINCT Query

A DISTINCT query in SQL is used to retrieve unique values from a specific column or combination of columns in a table. It removes duplicate rows from the result set, ensuring that each row returned by the query contains unique values.

The basic syntax of a SELECT query with DISTINCT is as follows:

```sql
Copy code
SELECT DISTINCT column1, column2, ...
FROM table_name;
```
Where:

SELECT DISTINCT is the keyword combination indicating that you want to retrieve unique values.
column1, column2, ... are the columns from which you want to retrieve unique values. You can specify one or more columns.

For example, suppose you have a table named orders with a column named product_id that contains duplicate entries. To retrieve the unique product IDs from the orders table, you can use the following query:

```sql
Copy code
SELECT DISTINCT product_id
```
FROM orders;
This query will return only distinct values of product_id from the orders table, removing any duplicate entries.

You can also use the DISTINCT keyword with multiple columns to retrieve unique combinations of values across those columns. For example:

```sql
Copy code
SELECT DISTINCT column1, column2
FROM table_name;
```
This query will return unique combinations of values from column1 and column2 in the result set, removing duplicate combinations.

It's important to note that using DISTINCT can affect the performance of the query, especially on large datasets, as the database engine needs to perform additional processing to identify and remove duplicate rows.

# COUNT 

The COUNT function in SQL is used to count the number of rows that match a specified condition within a table or result set. It is commonly used to determine the number of records in a table or to calculate the number of rows that meet certain criteria.

The basic syntax of the COUNT function is as follows:

```sql
Copy code
SELECT COUNT(*)
FROM table_name;
```
This query will return the total number of rows in the specified table.

You can also use the COUNT function with a specific column to count the number of non-null values in that column:

```sql
Copy code
SELECT COUNT(column_name)
FROM table_name;
```

This query will count the number of non-null values in the specified column of the table.

Additionally, you can use the COUNT function with a WHERE clause to count the number of rows that meet specific conditions:

```sql
Copy code
SELECT COUNT(*)
FROM table_name
```
WHERE condition;

For example, if you have a table named employees and you want to count the number of employees with a salary greater than 50000, you can use the following query:

```sql
Copy code
SELECT COUNT(*)
FROM employees
WHERE salary > 50000;
```

The COUNT function can also be combined with other SQL functions and clauses, such as DISTINCT, GROUP BY, HAVING, and JOIN, to perform more complex calculations and analysis on the data.

It's important to note that the COUNT function always returns an integer value representing the number of rows that match the specified condition. If there are no matching rows, COUNT will return 0.

# WHERE CLAUSE
 "where" clause is used to specify a condition while retrieving data from a database. It allows you to filter records based on specified criteria. Here's a basic example:

```sql
Copy code
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
Copy code
SELECT name
FROM employees
WHERE department = 'Sales';
```
This query will return the names of all employees where the department column equals 'Sales'. The "where" clause allows you to narrow down your results to only include records that meet specific criteria.


**Equality: Check if a column is equal to a specific value.**

```sql
Copy code
WHERE column_name = value
```
**Inequality: Check if a column is not equal to a specific value.**

```sql
Copy code
WHERE column_name <> value
```
**Range: Check if a column's value falls within a range.**

```sql
Copy code
WHERE column_name BETWEEN value1 AND value2
```
**NULL: Check if a column is NULL.**

```sql
Copy code
WHERE column_name IS NULL
```
**NOT NULL: Check if a column is not NULL.**

```sql
Copy code
WHERE column_name IS NOT NULL
```
**Pattern Matching: Use wildcards to search for patterns in string values.**

```sql
Copy code
WHERE column_name LIKE 'pattern'
```
**Logical Operators: Use logical operators (AND, OR, NOT) to combine conditions.**

```sql
Copy code
WHERE condition1 AND condition2
WHERE condition1 OR condition2
WHERE NOT condition
```
**IN: Check if a column's value is within a list of specified values.**

```sql
Copy code
WHERE column_name IN (value1, value2, ...)
```
**NOT IN: Check if a column's value is not within a list of specified values.**

```sql
Copy code
WHERE column_name NOT IN (value1, value2, ...)
```