# Introduction to SQL with Snowflake

Welcome to the world of SQL using Snowflake! This guide will introduce you to the basics of SQL and how to use Snowflake for managing and querying data.

## What is SQL?
SQL (Structured Query Language) is a standard programming language specifically designed for managing data held in a relational database management system. It is used for tasks such as querying, updating, and managing data.

## Why Snowflake?
Snowflake is a cloud-based data warehousing platform that supports a wide range of standard SQL features. Its unique architecture allows for easy scalability, concurrency, and flexibility in data processing and analysis.

# Setting Up Snowflake

To begin our journey with SQL and data management, it's essential to set up a Snowflake account and familiarize yourself with the Snowflake Web Interface. Snowflake is a cloud-based data platform that provides powerful data warehousing and analytics capabilities.

## Creating a Snowflake Account

If you don't have a Snowflake account yet, follow these steps:

1. **Visit the Snowflake Website**: Go to [Snowflake's official website](https://www.snowflake.com/).

2. **Sign Up for an Account**: Look for the option to sign up or start a free trial. Snowflake often offers a free trial period which is great for getting started.

3. **Complete the Registration**: Fill in the required details such as your email, company name (if applicable), and other necessary information.

4. **Verification**: After registration, you may need to verify your email address to activate your account.

5. **Log In**: Once your account is set up and verified, log in to access the Snowflake Web Interface.

## Accessing the Snowflake Web Interface

The Snowflake Web Interface is where you'll interact with your Snowflake instance. It's a user-friendly environment where you can execute SQL queries, create databases, and manage your data.

1. **Navigate to the Web Interface**: Use the link provided during your account setup or go to the [Snowflake login page](https://app.snowflake.com/).

2. **Enter Your Credentials**: Log in with your Snowflake username and password.

## Creating a Database and Schema in Snowflake

Once logged in, the next step is to create a database and a schema. This is where your data will be stored and organized.

1. **Login to Snowflake**: If you're not already logged in, log into the Snowflake Web Interface with your credentials.

2. **Create Database**:
    Execute the following SQL command in the Snowflake interface to create a new database named 'ironhack_dapt'.

    ```sql
    CREATE DATABASE ironhack_dapt;
    ```

    This command creates a new database where you can store and manage your data.

3. **Create Schema**:
    In the newly created 'ironhack_dapt' database, create a schema named 'ironhack_class'.

    ```sql
    USE DATABASE ironhack_dapt;
    CREATE SCHEMA ironhack_class;
    ```

    A schema is like a folder within your database. It helps in organizing and segregating different tables and data objects.

With your Snowflake account set up and your database and schema ready, you're all set to start creating tables and exploring SQL queries.

# Creating Tables in Snowflake

In this section, we will focus on creating tables in Snowflake, which forms the foundation of storing and managing data in a database. A table in a database is similar to a table in a spreadsheet; it stores data in rows and columns. Each table contains data about a particular subject, such as customers, products, or sales.

Creating tables is a crucial first step in database management. It involves defining the table's name, the columns it contains, and the type of data each column will hold. This structure helps us organize data efficiently and allows for effective data retrieval and manipulation.

For our class, we will create tables corresponding to the datasets provided. These datasets represent different aspects of a typical business environment, such as customer information, product details, sales records, and more. By creating tables for each dataset, we will have a well-structured database that mimics real-world data scenarios.

We will start by creating a table for each dataset, specifying the appropriate data types for each column and ensuring the structure aligns with the data we have. Once these tables are set up, we will explore how to insert, update, query, and manage the data within them.

Let's begin by creating our first table in Snowflake.

## Create Customer Table

To create the 'Customer' table in the 'ironhack_class' schema, use the following command:

    ```sql
    USE SCHEMA ironhack_dapt.ironhack_class;
    CREATE TABLE Customer (
        CustomerID VARCHAR(50),
        CustomerName VARCHAR(100),
        Segment VARCHAR(50),
        Age INT,
        Country VARCHAR(50),
        City VARCHAR(50),
        State VARCHAR(50),
        PostalCode INT,
        Region VARCHAR(50)
    );
    ```


## Create Product Table

Use this command to create the 'Product' table in the 'ironhack_class' schema.

    ```sql
    CREATE TABLE Product (
        ProductID VARCHAR(50),
    	Category VARCHAR(50),
    	SubCategory VARCHAR(50),
    	ProductName VARCHAR(200)
	);
    ```

## Create Sales Table

Here's the SQL command for creating the 'Sales' table:

    ```sql
    CREATE TABLE Sales (
        OrderLine INT,
        OrderID VARCHAR(50),
        OrderDate DATE,
        ShipDate DATE,
        ShipMode VARCHAR(50),
        CustomerID VARCHAR(50),
        ProductID VARCHAR(50),
        Sales DECIMAL,
        Quantity INT,
        Discount DECIMAL,
        Profit DECIMAL
    );
    ```
## Create Student Table

To create the 'Student' table, use this command:

    ```sql
    CREATE TABLE Student (
        EnrollmentNO INT,
        Name VARCHAR(100),
        ScienceMarks INT
    );
    ```

# Understanding Primary and Foreign Keys in SQL

In this section, we delve into the concepts of Primary Keys and Foreign Keys, essential components of relational databases. These keys play a crucial role in maintaining data integrity and establishing relationships between tables.

## Primary Keys

A primary key uniquely identifies each row in a table. It is crucial for ensuring the uniqueness of records and plays a vital role in database indexing.

### Characteristics of Primary Keys
- **Uniqueness**: No two rows can have the same primary key value.
- **Non-Nullability**: A primary key cannot be NULL.

### Example in Context
In our 'Customer' table, the `CustomerID` column serves as the primary key. Each customer has a unique ID.

```plaintext
| Customer ID | First Name | Last Name | Age |
|-------------|------------|-----------|-----|
| V_001       | Jay        | Pee       | 23  |
| V_002       | Kay        | Qu        | 23  |
| ...         | ...        | ...       | ... |
```

## Foreign Keys

Foreign keys establish a crucial link between two tables in a relational database. They refer to the primary key in another table, creating a relationship between the two. This relationship is foundational in maintaining the referential integrity of your data.

### Example in Context
Consider the 'Order' table in our database. The `CustomerID` field in this table is a foreign key that refers to the `CustomerID` in the 'Customer' table. This connection allows us to understand which customer made each order.

```plaintext
| Order ID | Customer_ID | Product_key | Value |
|----------|-------------|-------------|-------|
| O_001    | V_001       | P_001_01    | 65    |
| O_002    | V_001       | P_001_02    | 23    |
| ...      | ...         | ...         | ...   |
```

In this structure, `Customer_ID` in the 'Order' table links each order to a specific customer in the 'Customer' table, facilitating queries that combine data from both tables.

## Understanding Table Relationships

In relational databases, the way tables are related to each other is crucial for designing efficient database schemas and writing effective SQL queries.

### Types of Relationships
- **One-to-One**: Each row in one table corresponds to exactly one row in another table. This relationship is less common but important in certain scenarios.
- **One-to-Many**: A single row in one table may correspond to multiple rows in another table. This is a very common relationship type in databases.
- **Many-to-Many**: Rows in one table can relate to multiple rows in another table, and vice versa. Typically, this relationship requires an intermediate table to effectively manage the connections.

## Application in Snowflake

Snowflake's platform supports the definition and use of primary and foreign keys, which are fundamental for defining relationships between tables.

### Primary and Foreign Keys in Snowflake
- While Snowflake allows you to define primary and foreign keys, it does not enforce foreign key constraints. This means that Snowflake will not prevent you from entering inconsistent data.
- Despite this, it is crucial to understand and use these keys for maintaining data integrity and for effective query writing, particularly when performing joins between tables.

## Key Takeaways

- **Primary Keys**: Essential for uniquely identifying each row in a table. They are the cornerstone of table integrity.
- **Foreign Keys**: Establish relationships between tables and are crucial for joins in SQL queries. They help in maintaining relational data integrity.
- **Understanding Relationships**: Grasping the concepts of primary and foreign keys, and the types of relationships they facilitate, is key to understanding how data is structured and interconnected in relational databases.

Appreciating these concepts will empower you to design more effective database schemas and write more efficient SQL queries, especially in a platform like Snowflake.

## Introduction to SQL Queries

SQL, or Structured Query Language, is a powerful tool used in the world of data management and analysis. As the standard language for interacting with relational databases, SQL enables you to efficiently perform various operations on data stored in databases. In the realm of cloud-based data warehousing platforms like Snowflake, SQL plays a pivotal role in data retrieval and manipulation.

### What is SQL?

SQL is a domain-specific language used in programming and managing data held in a relational database management system (RDBMS). It is particularly useful for handling structured data, where there are relations between different entities/variables of the data.

#### Key Features of SQL
- **Versatility**: SQL is used to query, insert, update, and delete data — making it incredibly versatile for various data operations.
- **Interactivity**: SQL allows for real-time interaction with the database, enabling immediate feedback and results.
- **Standardization**: SQL is standardized, meaning that its core commands are used across various database systems with minimal variation.

### Why SQL in Snowflake?

Snowflake is a cloud-based data platform that offers a wide array of features for data storage, processing, and analysis. Using SQL in Snowflake allows you to:

- Access and analyze large volumes of data efficiently.
- Leverage Snowflake's computing power to perform complex queries.
- Utilize Snowflake's unique architecture, which separates storage and compute, allowing for scalable and cost-effective data processing.


## SELECT Statements: The Gateway to Data Retrieval

The SELECT statement is a fundamental component of SQL, primarily used for data retrieval from a database. It is the most basic yet powerful tool in SQL for querying and extracting data.

### Understanding SELECT Statements

- **Purpose**: The SELECT statement is used to select specific data from one or more tables in a database.
- **Flexibility**: You can choose to extract all columns from a table or specify particular columns.
- **Combination with Other Clauses**: SELECT statements can be combined with various clauses (like WHERE, JOIN, ORDER BY) to refine and customize data retrieval.

### Basic Syntax
```sql
SELECT column_name1, column_name2 FROM table_name;
```

### Examples
Selecting a single column:
```sql
SELECT first_name FROM customer_table;
```
Selecting multiple columns:
```sql
SELECT first_name, last_name FROM customer_table;
```
Selecting all columns:
```sql
SELECT * FROM customer_table;
```

## Using DISTINCT

In SQL, the `DISTINCT` keyword plays a crucial role in data retrieval operations, particularly when you need to eliminate duplicate entries in your result set. It ensures that the results returned from your query are unique, providing clarity and precision in data analysis.

### What is DISTINCT?

The `DISTINCT` keyword is used in conjunction with the `SELECT` statement in SQL. Its primary purpose is to remove duplicate records from the result set and return only unique entries.

### Key Characteristics of DISTINCT
- **Elimination of Duplicates**: `DISTINCT` ensures that each row in your result set is different from all others.
- **Enhanced Data Clarity**: By removing duplicates, it offers a clearer view of the data, which is particularly useful in analytics and reporting.
- **Applicability**: It can be applied to one or more columns in your SQL query.

### Basic Syntax
The syntax for using DISTINCT is straightforward. It is placed immediately after the `SELECT` keyword.

### Syntax
```sql
SELECT DISTINCT column_name FROM table_name;
```

### Example
Selecting distinct values from one column:
```sql
SELECT DISTINCT customer_name FROM customer_table;
```
Selecting distinct values from multiple columns:
```sql
SELECT DISTINCT customer_name, age FROM customer_table;
```

## The WHERE Clause

The `WHERE` clause in SQL is a powerful tool for filtering data. It allows you to specify conditions that the data must meet to be included in the query results. This clause is essential for refining your data retrieval and making your queries more precise.

### What is the WHERE Clause?

In SQL, the `WHERE` clause is used to filter records from a table, a view, or a join, based on specified conditions. It helps in narrowing down the data that you want to retrieve or manipulate.

#### Functionality of the WHERE Clause
- **Condition-Based Filtering**: Only rows that meet the specified conditions are returned in the result set.
- **Enhanced Query Precision**: By using the `WHERE` clause, you can avoid retrieving unnecessary data, making your queries more efficient and your results more relevant.

### Basic Syntax
The `WHERE` clause follows the `FROM` clause in a `SELECT` statement.

### Syntax
```sql
SELECT column_name FROM table_name WHERE condition;
```

### Example
Selecting with a condition:
```sql
SELECT first_name FROM customer_table WHERE age = 25;
```

## AND, OR, and NOT Operators

In SQL, the operators AND, OR, and NOT are essential for creating more complex query conditions. These logical operators allow you to combine, negate, or refine multiple conditions in your queries, offering a higher degree of control over the data you retrieve.

###  The Role of Logical Operators

Logical operators in SQL are used to enhance the capabilities of the WHERE clause, allowing for more sophisticated data filtering. Here's a brief overview of each:

- **AND**: Used to combine multiple conditions, where each condition within the AND must be true for the row to be included in the result set.
- **OR**: Used to combine multiple conditions, where at least one of the conditions must be true for the row to be included.
- **NOT**: Used to negate a condition, meaning the condition opposite to what is stated is considered.

###  Using AND, OR, and NOT in Queries

####  AND Operator

The AND operator is used when you want to retrieve records that satisfy all the given conditions.

### Syntax
Using AND:
```sql
SELECT column_name FROM table_name WHERE condition1 AND condition2;
```
Using OR:
```sql
SELECT column_name FROM table_name WHERE condition1 OR condition2;
```
Using NOT:
```sql
SELECT column_name FROM table_name WHERE NOT condition;
```

### Example
Using AND to combine conditions:
```sql
SELECT first_name, last_name FROM customer_table WHERE age > 20 AND age < 30;
```
Using OR to expand conditions:
```sql
SELECT first_name, last_name FROM customer_table WHERE age < 20 OR age > 30;
```
Using NOT to negate conditions:
```sql
SELECT first_name, last_name FROM customer_table WHERE NOT age = 25;
```

## INSERT INTO Statement

The `INSERT INTO` statement is a fundamental part of SQL, used for adding new records (rows) to a table in a database. Understanding how to use this statement is crucial for managing and updating the data in your databases.

### What is the INSERT INTO Statement?

The `INSERT INTO` statement allows you to insert new data into a table. Each row in a table represents a record, and with `INSERT INTO`, you can add new records with specified values in the columns.

#### Key Characteristics of INSERT INTO
- **Flexibility**: You can choose to insert values into all columns or specify which columns to populate.
- **Data Integrity**: When inserting data, it's important to ensure that the new data adheres to the constraints set in the table schema (like data types, NOT NULL constraints, etc.).

### Basic Syntax
The basic syntax of the `INSERT INTO` statement varies slightly depending on whether you're inserting data into all columns or specific columns.

### Syntax
```sql
INSERT INTO table_name (column1, column2) VALUES (value1, value2);
```

### Example
- Inserting a single row:
```sql
INSERT INTO customer_table (cust_id, first_name, age, email_id) VALUES (2, 'Dee', 22, 'd@xyz.com');
```
Inserting multiple rows:
```sql
INSERT INTO customer_table VALUES (1, 'Ee', 'Ef', 35, 'ef@xyz.com'), (1, 'Gee', 'Eh', 42, 'gh@xyz.com');
```
## ALTER TABLE Statement

The `ALTER TABLE` statement in SQL is a versatile command used to modify the structure of an existing table in various ways. It allows you to adapt the table structure as your data requirements change over time.

The `ALTER TABLE` statement is essential for changing a table's definition or structure without needing to delete and recreate the table. This capability is crucial for maintaining and updating databases dynamically.

### Basic Syntax
```sql
ALTER TABLE table_name
[Specify Actions];
```

### Possible Actions
- **Columns**: Add, delete, modify, or rename columns.
- **Constraints**: Add or drop constraints like NOT NULL, CHECK, or FOREIGN KEY.
- **Index**: Add or drop indexes (not covered in this lecture).

### Modifying Columns

#### Adding a Column
To add a new column to a table, you specify the column name and its data type.

##### Syntax
```sql
ALTER TABLE table_name
ADD column_name Data_Type;
```
#### Dropping a Column
To remove a column from a table, you specify the column name.

##### Syntax
```sql
ALTER TABLE table_name
DROP column_name;
```
### Modifying and Renaming Columns

#### Modifying a Column's Data Type
To change the data type of a column, you specify the column and the new data type.

##### Syntax
```sql
ALTER TABLE table_name
ALTER COLUMN column_name TYPE New_Data_Type;
```
#### Renaming a Column
To rename a column, you specify the current column name and the new name.

##### Syntax
```sql
ALTER TABLE table_name
RENAME COLUMN column_1 TO column_2;
```
### Adding and Dropping Constraints

#### Setting a NOT NULL Constraint
To enforce that a column cannot have NULL values, use the SET NOT NULL constraint.

##### Syntax
```sql
ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;
```
#### Dropping a NOT NULL Constraint
To remove a NOT NULL constraint from a column, use DROP NOT NULL.

##### Syntax
```sql
ALTER TABLE table_name ALTER COLUMN column_name DROP NOT NULL;
```
#### Adding a CHECK Constraint
To add a condition that the data in a column must satisfy, use the CHECK constraint.

##### Syntax
```sql
ALTER TABLE table_name ADD CONSTRAINT column_name CHECK (column_name >= 100);
```
#### Setting a Primary Key
To designate a column as the primary key, use the following syntax.

##### Syntax
```sql
ALTER TABLE table_name ADD PRIMARY KEY (column_name);
```

### Adding a Foreign Key Constraint
To create a foreign key relationship with another table, use the FOREIGN KEY constraint.

#### Syntax
```sql
ALTER TABLE child_table ADD CONSTRAINT child_column
FOREIGN KEY (parent_column) REFERENCES parent_table;
```
## IN Statement
The `IN` condition in SQL is a powerful tool for specifying multiple values in a `WHERE` clause. It is particularly useful for simplifying queries that would otherwise require multiple `OR` conditions.
The `IN` condition in SQL allows you to specify a list of values that a column can match to be included in the results. It is a shorthand for a series of `OR` conditions, making your queries more concise and readable.

### Basic Syntax of IN
```sql
SELECT column_name FROM table_name WHERE column_name IN (value1, value2, ...);
```

### Example of Using IN
 **Simple IN Condition**:
```sql
SELECT * FROM customer WHERE city IN ('Philadelphia', 'Seattle');
```
This query selects all records from the `customer` table where the `city` column has a value of either 'Philadelphia' or 'Seattle'.

### Benefits of Using IN
- **Simplicity**: Reduces complexity in queries that would require multiple `OR` conditions.
- **Readability**: Makes the query more readable and easier to understand.
- **Efficiency**: In some cases, using `IN` can be more efficient than using multiple `OR` conditions.

## When to Use the IN Condition

- **Filtering on Multiple Values**: Use `IN` when you need to filter a column on a list of multiple specific values.
- **Substituting for Multiple OR Conditions**: Replace multiple `OR` conditions with an `IN` clause for cleaner, more manageable SQL code.

### Comparison with OR Conditions

The `IN` condition is functionally similar to using multiple `OR` conditions but with improved readability and simplicity. For example:

### Using OR
```sql
SELECT * FROM customer WHERE city = 'Philadelphia' OR city = 'Seattle';
```
### Using IN
```sql
SELECT * FROM customer WHERE city IN ('Philadelphia', 'Seattle');
```
Both queries produce the same result, but the `IN` condition simplifies the query.


## BETWEEN statement

The `BETWEEN` condition in SQL is a valuable tool for filtering records based on a range of values. It simplifies the syntax for specifying a range in queries, making your SQL statements more readable and efficient.

The `BETWEEN` condition allows you to select data that falls within a specified range. This can be numeric values, text values (based on alphabetical order), or dates. It's an inclusive range, meaning it includes the start and end values specified.

### Basic Syntax of BETWEEN
```sql
SELECT column_name FROM table_name WHERE column_name BETWEEN value1 AND value2;
```

### Examples of Using BETWEEN
- **Numeric Range**:
  ```sql
  SELECT * FROM customer WHERE age BETWEEN 20 AND 30;
  ```
  This query will return all customers whose age is between 20 and 30, including those who are exactly 20 or 30 years old.

- **Date Range**:
  ```sql
  SELECT * FROM sales WHERE ship_date BETWEEN '2015-04-01' AND '2016-04-01';
  ```
  This query retrieves all sales records with a shipping date between April 1, 2015, and April 1, 2016.

### Using NOT with BETWEEN
You can also use `NOT BETWEEN` to exclude a range of values.

#### Example
```sql
SELECT * FROM customer WHERE age NOT BETWEEN 20 AND 30;
```
This query will return customers who are either younger than 20 or older than 30.

### Comparing BETWEEN with Standard Operators
The `BETWEEN` condition is equivalent to a combination of `>=` and `<=` operators. For example:

```sql
SELECT * FROM customer WHERE age BETWEEN 20 AND 30;
```

Is the same as:

```sql
SELECT * FROM customer WHERE age >= 20 AND age <= 30;
```

### Benefits of Using BETWEEN
- **Simplicity**: Reduces the complexity of queries that involve ranges.
- **Readability**: Enhances the readability of SQL queries, making them easier to understand and maintain.
- **Versatility**: Can be used with various data types, including numbers, dates, and strings.

## LIKE statement

The `LIKE` condition in SQL is an incredibly useful tool for performing pattern matching in queries. It's especially handy when you want to search for data with specific patterns within a column.

The `LIKE` condition in SQL is used for pattern matching and is employed in a `WHERE` clause to search for a specified pattern in a column.

### Basic Syntax of LIKE
```sql
SELECT column_name FROM table_name WHERE column_name LIKE pattern;
```

### Wildcards in LIKE
Wildcards are special characters used in the `LIKE` condition to represent one or more characters in the pattern matching. The most commonly used wildcards are `%` and `_`.

- **% Wildcard**: Represents any sequence of characters (including zero characters).
  - `A%` means any string that starts with 'A'.
  - `%A` means any string that ends with 'A'.
  - `A%B` means any string that starts with 'A' and ends with 'B'.

- **_ Wildcard**: Represents a single character.
  - `AB_C` means any string that starts with 'AB', followed by any one character, and then 'C'.

### Examples of Using LIKE
**Starting with a Specific Pattern**:
```sql
SELECT * FROM customer_table WHERE first_name LIKE 'Jo%';
```
This query will find all records where the first name starts with 'Jo'.

**Containing a Specific Pattern**:
```sql
SELECT * FROM customer_table WHERE first_name LIKE '%od%';
```
This query will find all records where the first name contains 'od'.

**Matching a Specific Pattern with a Single Character**:
```sql
SELECT first_name, last_name FROM customer_table WHERE first_name LIKE 'Jas_n';
```
This query will find records where the first name matches the pattern 'Jas' followed by any one character, and then 'n'.

**Excluding a Specific Pattern**:
```sql
SELECT first_name, last_name FROM customer_table WHERE last_name NOT LIKE 'J%';
```
This query will find all records where the last name does not start with 'J'.

**Escaping Wildcards**:
```sql
SELECT * FROM customer_table WHERE last_name LIKE 'G\%';
```
 This query will find all records where the last name actually starts with 'G%'.

## ORDER BY statement

The `ORDER BY` clause in SQL is an essential tool for sorting records in your result set. It can be used in conjunction with `SELECT` statements to organize the retrieved data in a specific order, either ascending or descending.

The `ORDER BY` clause allows you to sort the data returned by a `SELECT` query in either ascending (ASC) or descending (DESC) order based on one or more columns. By default, `ORDER BY` sorts the data in ascending order.

### Basic Syntax of ORDER BY
```sql
SELECT column_name FROM table_name [WHERE condition] ORDER BY column_name [ASC | DESC];
```

### Ordering by Multiple Columns
It's possible to sort data based on more than one column. This provides a multi-level sort where the data is first sorted by the first column, then by the second, and so on.

#### Syntax for Multiple Columns
```sql
ORDER BY column_name1 [ASC | DESC], column_name2 [ASC | DESC];
```

### Examples of Using ORDER BY
**Sorting by a Single Column**:
```sql
SELECT * FROM customer WHERE state = 'California' ORDER BY Customer_name;
```
This query sorts customers from California by their names in ascending order (default).

**Sorting by Multiple Columns**:
```sql
SELECT * FROM customer WHERE age > 25 ORDER BY City ASC, Customer_name DESC;
```
This query sorts customers over 25 years old first by city in ascending order and then by name in descending order within each city.

**Sorting in Descending Order**:
```sql
SELECT * FROM customer ORDER BY age DESC;
```
This query sorts all customers by age in descending order.

### Tips for Using ORDER BY
- **Default Order**: If you don't specify ASC or DESC, the order is ascending by default.
- **Column Position**: You can also use column positions instead of names, e.g., `ORDER BY 1` would order by the first column in the select list.
- **Performance Considerations**: Sorting can be resource-intensive, especially for large datasets. It's important to use `ORDER BY` judiciously to ensure efficient query performance.

# LIMIT statement

The `LIMIT` statement in SQL is a simple yet powerful tool for controlling the number of records returned by a query. This feature is particularly useful for managing large datasets and optimizing query performance.

The `LIMIT` statement restricts the number of rows returned by a query. It's especially useful when you need to work with a subset of data or when implementing features like pagination in applications.

### Basic Syntax of LIMIT
```sql
SELECT column_names FROM table_name [WHERE conditions] [ORDER BY expression [ASC | DESC]] LIMIT row_count;
```

### Examples of Using LIMIT
**Limiting the Number of Records**:
```sql
SELECT * FROM customer WHERE age >= 25 ORDER BY age DESC LIMIT 8;
```
This query will return the top 8 oldest customers who are at least 25 years old, sorted in descending order by age.

**Combining LIMIT with ORDER BY**:
```sql
SELECT * FROM customer WHERE age >= 25 ORDER BY age ASC LIMIT 10;
```
This query will return the top 10 youngest customers who are at least 25 years old, sorted in ascending order by age.

### Benefits of Using LIMIT
- **Performance**: Reduces the load on the database by limiting the number of rows processed and returned.
- **Efficiency**: Useful for quickly testing queries or when you only need a specific number of rows.
- **Practicality**: Essential for implementing pagination in applications that display large datasets.

### Tips for Using LIMIT
- **Ordering**: Combine `LIMIT` with `ORDER BY` to control which subset of rows is returned.
- **Testing**: Use `LIMIT` to test queries on large tables without processing the entire table.
- **Pagination**: Implement pagination in your applications by using `LIMIT` with an offset.

## AS statement

The `AS` keyword in SQL is a simple yet powerful feature that allows you to assign aliases to columns or tables. This can make your queries more readable and can be particularly useful in complex queries involving multiple tables or subqueries.

The `AS` keyword is used for renaming a column or table within the scope of a specific SQL query. This renaming is referred to as an alias and does not affect the actual table or column names in the database.

### Basic Syntax of AS
```sql
SELECT column_name AS column_alias FROM table_name;
```

### Examples of Using AS
**Assigning an Alias to a Column**:
```sql
SELECT Cust_id AS 'Serial number', Customer_name AS name, Age AS Customer_age FROM Customer;
```
This query renames the `Cust_id` column as 'Serial number', `Customer_name` as 'name', and `Age` as 'Customer_age' in the output.

### Benefits of Using Aliases
- **Clarity**: Makes complex queries more understandable, especially when columns or tables have long or technical names.
- **Necessity in Joins**: Essential when joining tables with overlapping column names to avoid ambiguity.
- **Formatting Results**: Useful for formatting the output of a query for reporting purposes.

### Tips for Using AS
- **Readability**: Choose aliases that make the query's intent clear.
- **Optional Syntax**: The keyword `AS` is optional. You can simply use the alias name next to the column or table name.
- **No Permanent Change**: Remember that using an alias does not change the actual column or table name in the database; it's only for the scope of the query.

## COUNT statement

The `COUNT` function in SQL is a fundamental and widely used aggregate function that returns the count of an expression, typically the number of rows that match a specific condition.

The `COUNT` function is used to determine the number of rows in a table that satisfy certain criteria. It can be applied to any column, as well as to the entire table, and is especially useful in data analysis and reporting.

### Basic Syntax of COUNT
```sql
SELECT COUNT(column_name) FROM table_name;
```

### Examples of Using COUNT
**Counting All Rows in a Table**:
```sql
SELECT COUNT(*) FROM sales;
```
This query returns the total number of rows in the `sales` table.

**Counting Specific Rows Based on a Condition**:
```sql
SELECT COUNT(order_line) AS 'Number of Products Ordered', COUNT(DISTINCT order_id) AS 'Number of Orders' FROM sales WHERE customer_id = 'CG-12520';
```
This query counts the number of product orders and the distinct number of orders made by a specific customer.

### When to Use COUNT
- **Data Analysis**: To determine the size of a dataset or the number of records that meet certain criteria.
- **Reporting**: Useful in generating reports where totals and subtotals are required.
- **Checking Data**: To verify the number of entries in tables, especially after data manipulation operations like INSERT or DELETE.

### Tips for Using COUNT
- **Performance**: While `COUNT(*)` is often efficient, be mindful of performance when counting large datasets, especially when using `COUNT` on specific columns with conditions.
- **Using with DISTINCT**: Combine `COUNT` with `DISTINCT` to count unique values in a column.
- **Combining with Other Functions**: `COUNT` can be combined with other SQL aggregate functions like `SUM`, `AVG`, for more comprehensive data analysis.

## SUM statement

The `SUM` function in SQL is a crucial aggregate function used to calculate the total sum of a numeric column. It's especially valuable in data analysis for summarizing and aggregating data.

The `SUM` function allows you to add up all the values in a specific column, providing a total sum of those values. This function can be applied to numeric fields and is often used in conjunction with other SQL clauses like `WHERE` and `GROUP BY`.

### Basic Syntax of SUM
```sql
SELECT SUM(aggregate_expression) FROM tables [WHERE conditions];
```

### Examples of Using SUM
**Calculating Total Profit**:
```sql
SELECT SUM(Profit) AS 'Total Profit' FROM sales;
```
This query calculates the total profit from all sales.

**Summing Specific Values Based on a Condition**:
```sql
SELECT SUM(quantity) AS 'Total Quantity' FROM orders WHERE product_id = 'FUR-TA-10000577';
```
This query calculates the total quantity of a specific product sold.

### When to Use SUM
- **Data Analysis and Reporting**: To calculate totals for financial data, sales, inventory, etc.
- **Aggregating Data**: Useful in generating reports and insights where aggregate data is needed.
- **Combining with Grouping**: Often used with `GROUP BY` to summarize data in subgroups.

### Tips for Using SUM
- **Data Type**: Ensure the column you're summing is a numeric data type.
- **Combine with Other Functions**: `SUM` can be combined with other aggregate functions like `COUNT`, `AVG`, for more comprehensive data analysis.
- **Performance Considerations**: Be mindful of performance when summing large datasets or complex queries.

## AVG statement

The `AVG` function in SQL is an important aggregate function used to calculate the average value of a specified expression. It's widely used in data analysis to derive meaningful insights from numerical data.

The `AVG` function computes the average value from a set of numbers. It's applied to a column and returns the mean of the numeric values in that column. This function can be particularly useful in financial analysis, statistical data, and other areas where averages are important.

### Basic Syntax of AVG
```sql
SELECT AVG(aggregate_expression) FROM tables [WHERE conditions];
```
### Examples of Using AVG
**Calculating Average Age**:
```sql
SELECT AVG(age) AS 'Average Customer Age' FROM customer;
```
This query calculates the average age of customers.

**Computing Average Based on a Calculated Value**:
```sql
SELECT AVG(sales * 0.10) AS 'Average Commission Value' FROM sales;
```
This query computes the average commission value, assuming the commission is 10% of sales.

### When to Use AVG
- **Analyzing Trends**: To understand trends in data, such as average sales over a period or average customer age.
- **Comparative Analysis**: For comparing averages across different groups or categories.
- **Financial Reporting**: Essential in financial scenarios for calculating average revenues, costs, or profits.

### Tips for Using AVG
- **Numeric Data Only**: The `AVG` function applies to numeric data types only.
- **Combining with GROUP BY**: Often used in conjunction with `GROUP BY` for segment-wise average calculations.
- **NULL Values**: `AVG` automatically excludes NULL values from the calculation.

## MIN & MAX statement

- **Purpose**: The `MIN()` and `MAX()` functions are essential tools in SQL, used for extracting the smallest and largest values from a selected column in a database table. These functions are particularly useful in various scenarios such as identifying extremes in data sets, like the highest or lowest salaries, prices, or scores.

- **MIN() Function**: 
  - The `MIN()` function returns the smallest value found in a specified column.
  - It's useful for identifying the "lowest" or "minimum" value in a range of data.
  - Common use cases include finding the lowest price of a product, the earliest date, or the smallest numerical value in a dataset.

- **MAX() Function**: 
  - In contrast, the `MAX()` function returns the largest value in a specified column.
  - It helps in determining the "highest" or "maximum" value.
  - Typical applications include finding the highest salary, the latest date, or the maximum numerical value.

### Syntax and Usage

```sql
-- Syntax for MIN function
SELECT MIN(column_name) FROM table_name;

-- Syntax for MAX function
SELECT MAX(column_name) FROM table_name;
```

- **Note**: Both functions can be used in the same SQL query and are often used in conjunction with other SQL clauses like `WHERE` to filter results.

### Example Queries with Explanation

1. **Finding the Minimum and Maximum Salary**
   Query to find the lowest and highest salary in an `employees` table:
   ```sql
   SELECT MIN(salary) AS MinSalary FROM employees;
   SELECT MAX(salary) AS MaxSalary FROM employees;
   ```
   These queries will scan the `salary` column in the `employees` table and return the smallest and largest values, respectively.

2. **Using MIN & MAX with WHERE Clause**
   Filtering results by department to find specific minimum and maximum values:
   ```sql
   SELECT MIN(salary) FROM employees WHERE department = 'Sales';
   SELECT MAX(salary) FROM employees WHERE department = 'Sales';
   ```
These queries will return the lowest and highest salaries, but only for employees in the 'Sales' department, demonstrating how `MIN` and `MAX` can be used with conditional logic.

## GROUP BY statement

The `GROUP BY` clause is a powerful tool in SQL used in a `SELECT` statement to group rows that have the same values in specified columns. It is often used with aggregate functions (COUNT, MAX, MIN, SUM, AVG) to perform calculations on each group of rows.

### Syntax of `GROUP BY`

```sql
SELECT column_name1, aggregate_function(column_name2)
FROM table_name
GROUP BY column_name1;
```

### Examples of `GROUP BY` Usage

1. **Counting Customers in Each Region**

   ```sql
   SELECT region, COUNT(customer_id) AS customer_count
   FROM customer
   GROUP BY region;
   ```

   This query counts the number of customers in each region.

2. **Summing Up Quantity Sold by Product**

   ```sql
   SELECT product_id, SUM(quantity) AS quantity_sold
   FROM sales
   GROUP BY product_id
   ORDER BY quantity_sold DESC;
   ```

   Here, the total quantity sold is summed up for each product.

3. **Aggregating Sales Data by Customer**

   ```sql
   SELECT customer_id,
          MIN(sales) AS min_sales,
          MAX(sales) AS max_sales,
          AVG(sales) AS average_sales,
          SUM(sales) AS total_sales
   FROM sales
   GROUP BY customer_id
   ORDER BY total_sales DESC
   LIMIT 5;
   ```
This query provides a comprehensive aggregation of sales data for each customer, showing minimum, maximum, average, and total sales.

## HAVING statement

The `HAVING` clause in SQL is used in combination with the `GROUP BY` clause. It allows you to specify a condition for the grouped rows returned by the `GROUP BY` clause. The `HAVING` clause is particularly useful for filtering groups based on the result of an aggregate function.

### Syntax of `HAVING`

```sql
SELECT ColumnNames, aggregate_function(expression)
FROM tables
[WHERE conditions]
GROUP BY column1
HAVING condition;
```

### Example of `HAVING` Usage

**Filtering Groups Based on a Condition**

```sql
SELECT region, COUNT(customer_id) AS customer_count
FROM customer
GROUP BY region
HAVING COUNT(customer_id) > 200;
```

This example demonstrates the use of the `HAVING` clause to filter out regions having less than 200 customers. It groups the data by region and counts the number of customers in each region, only including those regions where the count is greater than 200.
