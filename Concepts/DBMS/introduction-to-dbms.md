# Introduction to DBMS

## Data

Data is a collection of raw, unorganized facts and details like text, observations, figures, symbols,
and descriptions of things etc.

In other words, data does not carry any specific purpose and has no significance by itself.

### Types of Data

- Quantitative
    - Numerical form
    - Weight, volume, cost of an item.
- Qualitative
    - Descriptive, but not numerical.
    - Name, gender, hair color of a person.

## Information

Info. Is processed, organized, and structured data. It provides context of the data and enables decision making. Processed data that make sense to us. Information is extracted from the data, by analyzing and interpreting pieces of data.

## Data vs Information

| **Aspect**     | **Data**                              | **Information**                            |
| -------------- | ------------------------------------- | ------------------------------------------ |
| **Definition** | Raw facts and figures without context | Processed data with meaning and context    |
| **Nature**     | Unorganized and unprocessed           | Organized, structured, and meaningful      |
| **Purpose**    | Collected for reference or analysis   | Used for decision-making and understanding |
| **Context**    | Lacks context                         | Has clear context                          |
| **Form**       | Numbers, characters, symbols          | Sentences, statements, conclusions         |
| **Processing** | Not processed                         | Result of data processing                  |
| **Example**    | `{"Name": "Alice", "Score": 90}`      | `"Alice scored 90 in the test"`            |
| **Usefulness** | Not directly useful until processed   | Directly useful and insightful             |
| **Dependency** | Does not depend on information        | Depends on data                            |
| **Analogy**    | Raw ingredients                       | Cooked meal                                |

## Database

A database is an organized collection of structured data that can be easily accessed, managed, and updated electronically.

- Stores data in a structured format (like tables).
- Enables easy data retrieval, insertion, update, and deletion.
- Managed using a Database Management System (DBMS).
- Ensures data consistency, integrity, and security.
- Can handle large volumes of data efficiently.
- Examples include MySQL, MongoDB, PostgreSQL, etc.

## DBMS

A database-management system (DBMS) is a collection of interrelated data and a set of programs to access those data. The collection of data, usually referred to as the database, contains information relevant to an enterprise. The primary goal of a DBMS is to provide a way to store and retrieve database information that is both convenient and efficient.

A DBMS is the database itself, along with all the software and functionality. It is used to perform different operations, like addition, access, updating, and deletion of the data.

## DBMS vs File System

| **Aspect**              | **File System**                                              | **DBMS (Database Management System)**                            |
| ----------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| **Definition**          | A method of storing and managing data in flat files          | Software for managing databases with structured data             |
| **Data Organization**   | Data is stored in separate files without a defined structure | Data is organized in tables with rows and columns                |
| **Redundancy**          | High – same data may be stored in multiple files             | Low – uses normalization to reduce redundancy                    |
| **Data Integrity**      | Hard to enforce                                              | Enforced through constraints (like primary keys)                 |
| **Security**            | Basic file-level security                                    | Advanced security features like user roles and access control    |
| **Concurrency Control** | Not handled well                                             | Efficiently manages multiple users accessing data simultaneously |
| **Backup & Recovery**   | Manual and error-prone                                       | Automated and reliable                                           |
| **Data Retrieval**      | Slower and more complex                                      | Faster and easier via queries (like SQL)                         |
| **Examples**            | Text files, spreadsheets                                     | MySQL, PostgreSQL, MongoDB, Oracle                               |

### Problems in File system and DBMS solutions

| **File System Problem**                                                  | **DBMS Solution**                                                |
| ----------------------------------------------------------------------- | --------------------------------------------------------------- |
| **1. Data Redundancy** – Same data stored in multiple files             | **Normalization** reduces duplication and ensures consistency   |
| **2. Data Inconsistency** – Updates in one file not reflected in others | **Centralized data control** ensures updates reflect everywhere |
| **3. Lack of Data Integrity** – No constraints to maintain valid data   | **Integrity constraints** (e.g., primary keys, foreign keys)    |
| **4. Poor Data Security** – Basic or no access control                  | **User authentication and access control** in DBMS              |
| **5. No Concurrency Control** – Issues with multi-user access           | **Concurrency mechanisms** manage simultaneous users            |
| **6. Difficult Backup & Recovery** – Manual and error-prone             | **Automatic backup and recovery tools** in DBMS                 |
| **7. No Query Language** – Complex, slow data retrieval                 | **SQL** allows powerful and easy data querying                  |
| **8. No Data Relationships** – No link between files                    | **Relational model** manages data relationships efficiently     |
| **9. Poor Scalability & Performance** – Struggles with big data         | **Optimized indexing and query execution** improve performance  |
