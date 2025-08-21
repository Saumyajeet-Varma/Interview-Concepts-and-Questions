# Normalization

Normalization is the process of organizing data in a database to:

- Remove redundancy (duplicate data)
- Ensure data integrity (data remains accurate and consistent)
- Make data storage efficient

### Why do we need Normalization?

Let’s say we have this unorganized table of student data:

| StudentID | Name  | Course    | Instructor        |
| --------- | ----- | --------- | ----------------- |
| 1         | Rahul | DBMS      | Dr. Sharma        |
| 2         | Neha  | DBMS      | Dr. Sharma        |
| 3         | Rohan | OOP, DBMS | Dr. Verma, Sharma |

Problems here:

- Redundancy: "DBMS" and "Dr. Sharma" are repeated.
- Inconsistency: If someone types "Dr. Sarma" by mistake, it creates confusion.
- Update Anomalies: If Dr. Sharma changes their name, you have to update it everywhere.
- Insertion Anomalies: You can’t add a new instructor unless there's a student taking their course.
- Deletion Anomalies: If a student drops out, you might lose instructor/course info.

> Normalization solves all this.

### Benefits of Normalization

- Eliminates redundancy
- Saves space
- Improves data integrity
- Prevents anomalies (update, insert, delete)
- Makes data easier to maintain

### Drawbacks of Over-Normalization

- Too many tables → complex joins
- Slower reads (faster writes, though)

> So sometimes we denormalize (combine tables) for performance reasons (especially in analytics systems).

## Normal Forms

Normalization is done in stages, called Normal Forms. Each stage removes specific problems.

### 1st Normal Form (1NF) - Atomic values only

- Each column should have atomic (indivisible) values.
- No repeating groups or arrays.

#### Example

| StudentID | Name  | Courses   |
| --------- | ----- | --------- |
| 1         | Rahul | DBMS, OOP |
| 2         | Neha  | DBMS      |

> Problem: "Courses" has multiple values.

####  Solution (In 1NF):

| StudentID | Name  | Course |
| --------- | ----- | ------ |
| 1         | Rahul | DBMS   |
| 1         | Rahul | OOP    |
| 2         | Neha  | DBMS   |

> Each column has atomic values.

### 2nd Normal Form (2NF) — Remove Partial Dependency

- Must be in 1NF
- No partial dependency — i.e., non-key attributes should depend on whole primary key, not just a part.

#### Example

| StudentID | Course | StudentName | InstructorName |
| --------- | ------ | ----------- | -------------- |
| 1         | DBMS   | Rahul       | Dr. Sharma     |
| 2         | OOP    | Neha        | Dr. Verma      |

> Here, (StudentID + Course) is a composite key.
> - StudentName depends only on StudentID ✅
> - InstructorName depends only on Course ❌ → partial dependency!

#### Solution (In 2NF):

##### Students Table:

| StudentID | StudentName |
| --------- | ----------- |
| 1         | Rahul       |
| 2         | Neha        |

##### Courses Table:

| Course | InstructorName |
| ------ | -------------- |
| DBMS   | Dr. Sharma     |
| OOP    | Dr. Verma      |

##### Enrollment Table:

| StudentID | Course |
| --------- | ------ |
| 1         | DBMS   |
| 2         | OOP    |

> Now every non-key column depends on the whole key.

### 3rd Normal Form (3NF) — Remove Transitive Dependency

- Must be in 2NF
- No transitive dependency — i.e., non-key attributes should not depend on other non-key attributes

#### Example

| StudentID | StudentName | Department | HOD       |
| --------- | ----------- | ---------- | --------- |
| 1         | Rahul       | CS         | Dr. Jain  |
| 2         | Neha        | IT         | Dr. Mehra |

> Problem:
> - Department → HOD (transitive dependency)
> - HOD is indirectly dependent on StudentID.

#### Solution (In 3NF):

##### Students Table:

| StudentID | StudentName | Department |
| --------- | ----------- | ---------- |
| 1         | Rahul       | CS         |
| 2         | Neha        | IT         |

##### Departments Table:

| Department | HOD       |
| ---------- | --------- |
| CS         | Dr. Jain  |
| IT         | Dr. Mehra |

> Now every non-key attribute depends only on the key.

### Boyce-Codd Normal Form (BCNF) — Stronger 3NF

- Must be in 3NF
- Every determinant should be a candidate key

#### Example

| Course | Instructor | Room |
| ------ | ---------- | ---- |
| DBMS   | Dr. Sharma | 101  |
| OOP    | Dr. Verma  | 102  |

> Assume:
> - One course is taught by one instructor.
> - One instructor uses one room.
> Here:
> - Course → Instructor ✅
> - Instructor → Room ✅ ← But Instructor is not a candidate key!

#### Solution (In BCNF):

##### Courses Table:

| Course | Instructor |
| ------ | ---------- |
| DBMS   | Dr. Sharma |
| OOP    | Dr. Verma  |

##### Instructors Table:

| Instructor | Room |
| ---------- | ---- |
| Dr. Sharma | 101  |
| Dr. Verma  | 102  |

> Now every determinant is a candidate key

### 4th Normal Form (4NF)

- Must be in BCNF
- A relation should not have more than one independent multi-valued dependency

#### What is a Multi-Valued Dependency?

It happens when:
- A single attribute depends on the primary key,
- But independently of other attributes.

#### Example

| StudentID | Course | Hobby   |
| --------- | ------ | ------- |
| 1         | DBMS   | Cricket |
| 1         | DBMS   | Music   |
| 1         | OOP    | Cricket |
| 1         | OOP    | Music   |

> - Rahul (StudentID = 1) is enrolled in two Courses: DBMS, OOP
> - Rahul has two Hobbies: Cricket, Music
> Here:
> - Course and Hobby are independent but both depend on StudentID.
> This leads to redundancy: 4 rows to express 2 × 2 = 4 combinations.

#### Solution (In 4NF):

##### Students Table:

| StudentID | Course |
| --------- | ------ |
| 1         | DBMS   |
| 1         | OOP    |

##### Hobbies Table:

| StudentID | Hobby   |
| --------- | ------- |
| 1         | Cricket |
| 1         | Music   |

> Now, there are no independent multi-valued dependencies.

### 5th Normal Form (5NF)

also known as Project-Join Normal Form or PJNF

- Must be in 4NF
- A table should not have non-trivial join dependencies that are not implied by candidate keys

#### What is a Join Dependency?

It’s when a relation can be reconstructed by joining two or more projections, but those projections are not based on candidate keys.

#### Example

Imagine a consulting firm table:

| Consultant | Project | Skill  |
| ---------- | ------- | ------ |
| A          | X       | Java   |
| A          | X       | Python |
| A          | Y       | Java   |
| B          | Y       | Python |

> Here:
> - A can work on project X and Y.
> - A knows Java and Python.
> - B can work on Y and knows Python.
> But now we might get extra combinations if we try to break this into:

##### ConsultantProjects:

| Consultant | Project |
| ---------- | ------- |
| A          | X       |
| A          | Y       |
| B          | Y       |

##### ConsultantSkills:

| Consultant | Skill  |
| ---------- | ------ |
| A          | Java   |
| A          | Python |
| B          | Python |

##### ProjectSkills

| Project | Skill  |
| ------- | ------ |
| X       | Java   |
| X       | Python |
| Y       | Java   |
| Y       | Python |

> Joining these could lead to false tuples (e.g., B assigned to project X with Java skill, which is not true).

#### Solution (In 5NF):

| Normal Form | Fixes...                       | Rule                                        |
| ----------- | ------------------------------ | ------------------------------------------- |
| 1NF         | Non-atomic data (arrays, etc.) | Atomic values                               |
| 2NF         | Partial dependencies           | Full functional dependency on whole PK      |
| 3NF         | Transitive dependencies        | Non-key depends only on key                 |
| BCNF        | Candidate key anomalies        | Every determinant is a candidate key        |
| 4NF         | Multi-valued dependencies      | No independent multi-valued dependencies    |
| 5NF         | Join dependencies              | No spurious data after decomposition & join |

> Keep the original single table because it captures the three-way relationship correctly.
> So, in 5NF, either:
> - Decompose into smaller tables only if you can safely reconstruct original data, or
> - Keep the original table to prevent data distortion

### Summary Table

| Normal Form | Fixes...                       | Rule                                        |
| ----------- | ------------------------------ | ------------------------------------------- |
| 1NF         | Non-atomic data (arrays, etc.) | Atomic values                               |
| 2NF         | Partial dependencies           | Full functional dependency on whole PK      |
| 3NF         | Transitive dependencies        | Non-key depends only on key                 |
| BCNF        | Candidate key anomalies        | Every determinant is a candidate key        |
| 4NF         | Multi-valued dependencies      | No independent multi-valued dependencies    |
| 5NF         | Join dependencies              | No spurious data after decomposition & join |
