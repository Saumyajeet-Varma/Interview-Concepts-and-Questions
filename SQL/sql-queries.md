# SQL

It’s the standard language used to communicate with databases — mainly to store, retrieve, update, and delete data.

### Some basic things you can do with SQL:

- `SELECT` — get data from a database
- `INSERT` — add new data
- `UPDATE` — modify existing data
- `DELETE` — remove data
- `CREATE` — make new tables or databases
- `ALTER` — change structure of a table

## Using SQL in Your Web Site

To build a web site that shows data from a database, you will need:

- An RDBMS database program (i.e. MS Access, SQL Server, MySQL)
- To use a server-side scripting language, like PHP or ASP
- To use SQL to get the data you want
- To use HTML / CSS to style the page

## RDBMS

- RDBMS stands for Relational Database Management System.
- RDBMS is the basis for SQL, and for all modern database systems such as MS SQL Server, IBM DB2, Oracle, MySQL, and Microsoft Access.
- The data in RDBMS is stored in database objects called tables. A table is a collection of related data entries and it consists of columns and rows.

# SQL SELECT Statement

The `SELECT` statement is used to select data from a database.

```sql
SELECT column1, column2, ...
FROM table_name;
```

> Here, `column1`, `column2`, ... are the field names of the table you want to select data from. <br> The `table_name` represents the name of the table you want to select data from.

Example:

```sql
SELECT CustomerName, City FROM Customers;
```

If you want to return all columns, without specifying every column name, you can use the `SELECT *` syntax

```sql
SELECT * FROM Customers;
```

# SQL SELECT DISTINCT Statement

The `SELECT DISTINCT` statement is used to return only distinct (different) values.

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

Example:

```sql
SELECT DISTINCT Country FROM Customers;
```

# SQL WHERE Clause

The `WHERE` clause is used to filter records.

It is used to extract only those records that fulfill a specified condition.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

Example:

```sql
SELECT * FROM Customers
WHERE Country='India';
```

SQL requires single quotes around text values.
However, numeric fields should not be enclosed in quotes:

```sql
SELECT * FROM Customers
WHERE CustomerID=1;
```

## Operators in the WHERE Clause

| Operator | Description |
|----------|-------------|
| =        | Equal        |
| >        | Greater than |
| <        | Less than    |
| >=       | Greater than or equal |
| <=       | Less than or equal |
| <>       | Not equal (sometimes written as !=) |
| BETWEEN  | Between a certain range |
| LIKE     | Search for a pattern |
| IN       | Specify multiple possible values for a column |

# SQL ORDER BY Keyword

The `ORDER BY` keyword is used to sort the result-set in ascending or descending order.

- `ASC` - To sort the records in ascending order (by default)
- `DESC` - To sort the records in descending order

```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

Example:

```sql
SELECT * FROM Products
ORDER BY Price;
```

## ORDER BY Several Columns

```sql
SELECT * FROM Customers
ORDER BY Country, CustomerName;
```

> The following SQL statement selects all customers from the "Customers" table, sorted by the "Country" and the "CustomerName" column. This means that it orders by Country, but if some rows have the same Country, it orders them by CustomerName

```sql
SELECT * FROM Customers
ORDER BY Country ASC, CustomerName DESC;
```

> This  SQL statement selects all customers from the "Customers" table, sorted ascending by the "Country" and descending by the "CustomerName" column

# SQL AND Operator

The `WHERE` clause can contain one or many `AND` operators.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

Example:

```sql
SELECT *
FROM Customers
WHERE Country = 'India' AND CustomerName LIKE 'S%';
```

# SQL OR Operator

The `WHERE` clause can contain one or more `OR` operators.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 OR condition2 OR condition3 ...;
```

Example:

```sql
SELECT * FROM Customers
WHERE City = 'Bhubaneswar' OR CustomerName LIKE 'S%' OR Country = 'India';
```

> The `AND` operator displays a record if all the conditions are TRUE. <br> The `OR` operator displays a record if any of the conditions are TRUE.

## Combining AND and OR

You can combine the `AND` and `OR` operators.

```sql
SELECT * FROM Customers
WHERE Country = 'India' AND (CustomerName LIKE 'S%' OR CustomerName LIKE 'A%');
```

> The following SQL statement selects all customers from India that starts with a "S" or an "A".

> Make sure you use parenthesis to get the correct result, Without parenthesis, the select statement will return all customers from India that starts with a "S", plus all customers that starts with an "A", regardless of the country value

# SQL NOT Operator

The `NOT` operator is used in combination with other operators to give the opposite result, also called the negative result.

```sql
SELECT column1, column2, ...
FROM table_name
WHERE NOT condition;
```

Example:

```sql
SELECT * FROM Customers
WHERE NOT Country = 'India';
```

