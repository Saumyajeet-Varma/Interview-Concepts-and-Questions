## The SQL Unique Key

The SQL Unique Key (or, Unique constraint) does not allow duplicate values in a column of a table. It prevents two records from having same values in a column.

> Unique Key is just an alternative to the Primary Key; as both Unique and Primary Key constraints ensure uniqueness in a column of the table.

Suppose we have a table named CUSTOMERS to store the customer records in a Bank and if one of the column names is MOBILE_NO then, we can create a UNIQUE constraint on this column to prevent the entry of multiple records with the same mobile number.

### Features of Unique Key

- The unique key is similar to the primary key in a table, but it can accept NULL values, whereas the primary key does not.
- It accepts only one NULL value.
- It cannot have duplicate values.
- It can also be used as a foreign key in another table.
- A table can have more than one Unique column.

### Creating SQL Unique Key

You can create a Unique Key on a database table using the UNIQUE keyword in SQL. While creating a database table, specify this SQL keyword along with the column (where this key needs to be defined on).

#### Syntax

```sql
CREATE TABLE table_name(
   column1 datatype UNIQUE KEY,
   column2 datatype,
   .....
   .....
   columnN datatype
);
```

```sql
CREATE TABLE table_name(
   column1 datatype UNIQUE KEY,
   column2 datatype UNIQUE KEY,
   .....
   .....
   columnN datatype
);
```

#### Example

```sql
CREATE TABLE CUSTOMERS (
   ID INT NOT NULL UNIQUE KEY,
   NAME VARCHAR(20) NOT NULL,
   AGE INT NOT NULL,
   ADDRESS CHAR (25),
   SALARY DECIMAL (18, 2)
);
```

### Unique Key on an Existing Column

Until now, we have only seen how to define a Unique Key on a column while creating a new table. But, we can also add a unique key on an existing column of a table. This is done using the ALTER TABLE... ADD CONSTRAINT statement.

#### Syntax

```sql
ALTER TABLE table_name ADD CONSTRAINT 
UNIQUE_KEY_NAME UNIQUE (column_name);
```

> **NOTE** - Here the UNIQUE_KEY_NAME is just the name of the UNIQUE KEY. It is optional to specify and is used to drop the constraint from the column in a table.

#### Example

```sql
ALTER TABLE CUSTOMERS ADD CONSTRAINT 
UNIQUE_ADDRESS UNIQUE(ADDRESS);
```

### Dropping an SQL Unique Key

If you have already created a unique key on a column, you can drop it whenever it is not needed. To drop the Unique Key from the column of a table, you need to use the ALTER TABLE statement.

#### Syntax

```sql
ALTER TABLE table_name DROP CONSTRAINT UNIQUE_KEY_NAME;
```

#### Example

```sql
ALTER TABLE CUSTOMERS DROP CONSTRAINT UNIQUE_ADDRESS;
```

## The SQL Primary Key

The SQL Primary Key is a column (or combination of columns) that uniquely identifies each record in a database table. The Primary Key also speeds up data access and is used to establish a relationship between tables.

> Even though a table can only have one Primary Key, it can be defined on one or more fields. When a primary key is created on multiple fields of a table, it is called a Composite Key.

Let us say, you are developing an application called "Customer Management System" to handle all the customer data of a member-only resort. This data can include their personal details, assigned member IDs, other details of the membership they opted, etc. And in all the tables created within this database, the member ID is used to distinguish the customers from each other. So, this field will be the Primary Key.

### Features of Primary Key

- It contains only a unique value.
- It can not be null.
- One table can have only one Primary Key.
- A primary key length cannot be more than 900 bytes.

### Creating SQL Primary Key

While creating a table using the **CREATE TABLE statement**, you can add the primary key constraint on a particular column of the table just by to specifying the name of the column along with the keyword "PRIMARY KEY".

#### Syntax

```sql
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   PRIMARY KEY(column_name)
);
```

#### Example

```sql
CREATE TABLE CUSTOMERS (
   ID INT NOT NULL,
   NAME VARCHAR (20) NOT NULL,
   AGE INT NOT NULL,
   ADDRESS CHAR (25),
   SALARY DECIMAL (18, 2),       
   PRIMARY KEY (ID)
);
```

### Creating Primary Key on an Existing Column

We can also add the PRIMARY KEY constraint on an existing column of a table using the **ALTER TABLE** statement.

#### Syntax

```sql
ALTER TABLE table_name ADD CONSTRAINT PRIMARY KEY (column_name);
```

#### Example

```sql
ALTER TABLE CUSTOMERS ADD CONSTRAINT PRIMARY KEY(NAME);
```

### Dropping an SQL Primary Key

If you can add a Primary Key Constraint to a column in the table, you can drop it as well. This is done by using the ALTER TABLE... DROP statement.

#### Syntax

```sql
ALTER TABLE table_name DROP PRIMARY KEY;
```

#### Example

```sql
ALTER TABLE CUSTOMERS DROP PRIMARY KEY;
```

## The SQL Foreign Key

In SQL, a Foreign Key is a column in one table that matches a Primary Key in another table, allowing the two tables to be connected together.

A foreign key also maintains referential integrity between two tables, making it impossible to drop the table containing the primary key (preserving the connection between the tables).

> The foreign key can reference the unique fields of any table in the database. The table that has the primary key is known as the parent table and the key with the foreign key is known as the child table.

### Features of Foreign Key

- A Foreign Key is used to reduce the redundancy (or duplicates) in the table.
- It helps to normalize (or organize the data in a database) the data in multiple tables.

### Creating SQL Foreign Key

While creating a table using the CREATE TABLE statement, you can add the foreign key constraint on a particular column of the table by specifying the name of the column along with the keyword "FOREIGN KEY" and using the REFERENCES keyword to specify the referenced table and column.

#### Syntax

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
    CONSTRAINT fk_name 
	FOREIGN KEY (column_name) 
	REFERENCES referenced_table(referenced_column)
);
```

#### Example

```sql
CREATE TABLE CUSTOMERS(
   ID INT NOT NULL,
   NAME VARCHAR (20) NOT NULL,
   AGE INT NOT NULL,
   ADDRESS CHAR (25) ,
   SALARY DECIMAL (18, 2),       
   PRIMARY KEY (ID)
);
```

### Foreign Key Constraint on an Existing Column

We can also create a Foreign key constraint on a column of an existing table. This is useful when you forget to add a Foreign Key constraint on a column while creating a table, or when you want to add this constraint on another column even if one Foreign Key column exists in a table.

#### Syntax

```sql
ALTER TABLE TABLE2 
ADD CONSTRAINT[symbol] 
FOREIGN KEY(column_name) 
REFERENCES TABLE1(column_name);
```

#### Example

```sql
ALTER TABLE ORDERS 
ADD CONSTRAINT FK_ORDERS 
FOREIGN KEY(ID) 
REFERENCES CUSTOMERS(ID);
```

### Dropping a FOREIGN KEY

You can drop the foreign key from a table, without dropping that entire table, using the ALTER TABLE statement.

#### Syntax

```sql
ALTER TABLE table_name DROP FOREIGN KEY (constraint symbol);
```

#### Example

```sql
ALTER TABLE ORDERS DROP FOREIGN KEY FK_ORDERS;
```

### Primary key vs Foreign key

| Primary Key                                      | Foreign Key                                        |
|--------------------------------------------------|----------------------------------------------------|
| The primary key is always unique.                | The foreign key can be duplicated.                |
| The primary key can not be NULL.                 | The foreign key can be NULL.                      |
| A table can contain only one Primary Key.        | We can have more than one Foreign Key per table.  |

## The SQL Composite Key

An SQL Composite Key is a key that can be defined on two or more columns in a table to uniquely identify any record. It can also be described as a Primary Key created on multiple columns.

Composite Keys are necessary in scenarios where a database table does not have a single column that can uniquely identify each row from the table. In such cases, we might need to use the combination of columns to ensure that each record in the table is distinct and identifiable.

### Features of Composite key

- A Composite Key can be created by combining more than one Candidate Key.
- Each Candidate Key (or column) that makes up a Composite Key may or may not be a Foreign Key. However, if all the columns of the Composite Key are Foreign Keys in their own right, then the Composite Key is known as a Compound Key.
- A Composite Key cannot be NULL; i.e. any column of the Composite Key must not contain NULL values.
- The individual columns making up the Composite Key can contain duplicate values, but, the combination of these columns must be unique across the database table.

### Creating SQL Foreign Key

While creating a table using the CREATE TABLE statement, you can define a composite primary key by specifying multiple column names together in a PRIMARY KEY clause after all column definitions.

#### Syntax

```sql
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   CONSTRAINT composite_key_name,
   PRIMARY KEY(column_name)
);
```

#### Example

```sql
CREATE TABLE CUSTOMERS(
   ID INT NOT NULL,
   NAME VARCHAR (20) NOT NULL,
   AGE INT NOT NULL,
   ADDRESS CHAR (25),
   SALARY DECIMAL (18, 2),       
   CONSTRAINT ck_customers 
   PRIMARY KEY (ID, NAME)
);
```

### Dropping a Composite Key

You can drop the composite key from a table in MySQL database using the ALTER TABLE... DROP statement.

#### Syntax

```sql
ALTER TABLE table_name DROP PRIMARY KEY;
```

#### Example

```sql
ALTER TABLE CUSTOMERS DROP PRIMARY KEY;
```

## The SQL Alternate Key

SQL Alternate Keys in a database table are candidate keys that are not currently selected as a primary key. They can be used to uniquely identify a tuple(or a record) in a table.

There is no specific query or syntax to set the alternate key in a table. It is just a column that is a close second candidate which could be selected as a primary key. Hence, they are also called secondary candidate keys.

> If a database table consists of only one candidate key, that is treated as the primary key of the table, then there is no alternate key in that table.

### Features of Alternate Key

- The alternate key does not allow duplicate values.
- A table can have more than one alternate keys.
- The alternate key can contain NULL values unless the NOT NULL constraint is set explicitly.
- All alternate keys can be candidate keys, but all candidate keys can not be alternate keys.
- The primary key, which is also a candidate key, can not be considered as an alternate key.

## Keys in Table

### Candidate Key

A Candidate key is a subset of super keys that is used to uniquely identify records of a table. It can be a single field or multiple fields. The primary keys, alternate keys, foreign keys in a table are all types of candidate key.

### Primary Key

A Primary Key is a main key that is used to retrieve records from a table. It is a single column or field in a table that uniquely identifies each record in a database table.

### Foreign Key

The Primary key of one table will be the Foreign key in another table.

### Alternate Key

An Alternate key is a candidate key that could be a primary key but is not. Like primary key, it also uniquely identifies the records in a field of a table to retrieve row tuples from the said table. There can be a single or multiple fields identifying as alternate keys in a table.