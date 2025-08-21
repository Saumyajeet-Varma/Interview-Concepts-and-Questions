# Entity-Realtionship (ER) Model

It is a high level data model based on a perception of a real world that consists of a collection of basic objects, called entities and of relationships among these objects.

Graphical representation of ER Model is ER diagram, which acts as a blueprint of DB.

## Entity

An Entity is a “thing” or “object” in the real world that is distinguishable from all other objects.

- It has a physical existence.
- Entity can be uniquely identified. (By a primary attribute, aka Primary Key)
- **Strong Entity** - can be uniquely identified.
- **Weak Entity** - can't be uniquelu identified, depends on some other strong entity. It doesn’t have sufficient attributes, to select a uniquely identifiable attribute.
- **Entity set** - It is a set of entities of the same type that share the same properties, or attributes.
- E.g., Each student in a college is an entity, Student is an entity set.

## Attributes

- An entity is represented by a set of attributes.
- Each entity has a value for each of its attributes.
- For each attribute, there is a set of permitted values, called the domain, or value set, of that attribute.
- E.g., Student entity has following attributes -
    - Student_Id
    - Name
    - Course 
    - Batch
    - Contact
    - Address

### Types of Attributes

#### 1. Simple

Attributes which can’t be divided further.

E.g., Student_Id

#### 2. Composite

Attributes which can be divided into subparts (that is, other attributes).

E.g., Name of a person can be divided into First_Name, Middle_Name and Last_Name

#### 3. Single-valued

Only one value attribute.

E.g., Student_Id

#### 4. Multi-valued

Attribute having more than one value.

E.g., Phone_Number

Limit constraint may be applied, upper limit or lower limit.

#### 5. Derived

Value of this type of attribute can be derived from the value of other related attributes.

E.g., Age can be derived from DOB

#### 6. NULL

An attribute takes a null value when an entity does not have a value for it.

It may indicate “not applicable”, value doesn’t exist. 

E.g., person having no Middle_Name

It may indicate “unknown”.

## Relationships

- Association among two or more entities.
- E.g., Person has vehicle, Parent has Child, Customer borrow loan etc.
- **Strong Relationship**, between two independent entities.
- **Weak Relationship**, between weak entity and its owner/strong entity.
- **Degree of Relationship** - Number of entities participating in a relationship.
    - **Unary**, Only one entity participates. e.g., Employee manages Employee
    - **Binary**, Two entities participates. e.g., Student take Course 
    - **Ternary**, Three entities participates. e.g., Employee works on branch, Employee works on Job

### Relationship Constraints

#### Mapping Cardinality / Cardinality Ratio

Number of entities to which another entity can be assosiated via a relationship.

- **One to one** - One entity from entity set A can be associated with at most one entity of entity set B and vice versa.

<!-- img -->

- **One to many** - One entity from entity set A can be associated with more than one entities of entity set B however an entity from entity set B, can be associated with at most one entity.

<!-- img -->

- **Many to one** - More than one entities from entity set A can be associated with at most one entity of entity set B, however an entity from entity set B can be associated with more than one entity from entity set A.

<!-- img -->

- **Many to many** - One entity from A can be associated with more than one entity from B and vice versa.

<!-- img -->

#### Participation Constraints

Participation constraints (also known as existence dependencies) are rules in a relational database or ER model that specify whether the existence of an entity depends on being related to another entity via a relationship.

- **Total Participation (Mandatory)**
    - Every instance of the entity must be involved in the relationship.
    - Notation in ER diagrams: Double line connecting the entity to the relationship.
    - Example - Every student must be enrolled in at least one course.
- **Partial Participation (Optional)**
    - Some instances of the entity may or may not be involved in the relationship.
    - Notation: Single line connecting the entity to the relationship.
    - Example - Some employees may not be assigned to a project.

> Weak entity has total participation constraint, but strong may not have total.

## ER Notations

<!-- Imgs -->