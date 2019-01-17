# 1. Lecture 1: Entity-Relationship (ER) Models

## 1.1 Concepts of ER Model

An Entity-Relationship model (ER Model) describes iterrelated things of interest in a specific domain of knowledge.

- A basic ER model is composed of **entity types** (employee/department) and specifies **relationships** that can exist between entities (instances of those entity types).
- An ER model is commonly formed to represent things that a business needs to remember in order to perform business processes.
- Consequently, the ER model becomes an abstract data model, that defines a data or information structure which can be **implemented in a database**, typically a relational database.



## 1.2 Entity, Entity Type and Entity Set

1. Entity: Defined as a thing capable of an independent existence that can be uniquely identified and exists either *physically or logically*.Entities can be thought of as nouns. In relational databases, an entity refers to a single tuple.

   Example: a person exists physically while an order transaction exists logically.

2. Entity type: **defines** a collection of entities that have the same attributes.

3. Entity sets: a set of entities of the same type. In relational databases, an entity set refers to the tuples represented in the same table.

![entity-type-set](images/entity-type-set.png)

Type is a definition while set is a collection.



## 1.3 Relationship, Relationship Type and Relationship Set

1. Relationship: captures how entities are related to one another. Relationships can be thought of as verbs,  linking two or more nouns.

   Example: a `work_for` relationship between an employee and a department.

2. Relationship type: defines a relationship among entities of certain entity types. Relationship types are useful for capturing or expressing certain business rules.

3. The degree of a relationship type is the number of participating entity types. A binary relationship is a relationship type involving two entity types (degree=2). Ternary (degree=3).

4. Relationship set: a collection of relationships all belonging to one relationship type represented in the database.

   Example: if a relationship type is registration, each enrolment of a student in a course is an instance of registration and appears in the relationship set.

   ![relationship](images/relationship.png)



## 1.4 Attributes

Both entities and relationships can have attributes. For example, an employee has a Social Security Number (SSN) attribute, while a `work_for` relationship has a start date attribute.

A key attribute is a set of attributes (one or more) that uniquely identify an entity. i.e., no two entities may agree in their values for all of the attributes that constitute a key. For example, SSN is a single key attribute for employees. University ID and student ID are composite attributes to identify a university student in a country because student IDs may not be unique among universities in a country.



### 1.4.1 Types of Attributes

- **A simple attribute** has a single atomic value that does not contain any smaller meaningful components. For example, SSN and gender.

- **A composite attribute** is composed of several components. For example, address contains flat, block, street, city and country. Composition may form a hierarchy where some components are themselves composite.

  ![hierarchy-composite-attributes](images/hierarchy-composite-attributes.png)

- **A multi-valued attribute** has multiple values. For example, color of a product (red and white) and major of a student (computer science and mathematics).

- Ingeneral, composite and multi-valued attributes may be nested to any number of levels although this is rare. For example, a person can have multiple postal addresses.
- **A derived attribute** is an attribute whose value is calculated from other values. It does not need to be physically stored within the database. Instead, it can be derived by using an algorithm.



### 1.4.2 Value Sets (Domains) of Attributes

Each simple attribute is associated with a value set (or domain).

e.g. 1 data has a value of MM-DD-YYYY, where each letter is an integer.

e.g. 2 course grade has a value of {A+, A, A-, B+, B, B-, C+, C, C-, D, F}.

Value sets are similar to data types (int, double, boolean...) in most programming languages.



## 1.5 Constraints on Relationships

### 1.5.1 Participation Constraints

- Participation constraint indicates the minimum number of relationship instances that an entity can participate in.

- Total participation requires that each entity is involved in the relationship. In other words, an entity must exist related to another entity. In ER model, it is representaed by double lines.

  For example, every employee must work for a department. That is, the participation of employee in `work_for` relationship is total.

- Partial participation means that not all entities are involved in the relationship. Partial participation is represented by single lines in ER model.

  For example, some employees manage departments, i.e., the participation of employee in manage relationship is partial.



### 1.5.2 Cardinality Constraints

Cardinality ratio indicates the maximum number of relationship instances that an entity can participate in:

- A 1:1 relationship from entity type S to entity type T is one in which an entity from S is related to at most one entity from T and vice versa.
- An N:1 relationship from entity type S to entity type T is one in which an entity from T can be related to two or more entities from S.
- An 1:N relationship from entity type S to entity type T is one in which an entity from S can be related to two or more entities from T.
- An N:M relationship from entity type S to entity type T is one in which an entity from S can be related to two or more entities from T, and an entity from T can be related to two or more entities from S.



![n-1-work-for](images/n-1-work-for.png)

This is a N:1 relationship between EMPLOYEE and DEPARTMENT because many employees work for the same department.



![n-m-work-for](images/n-m-work-for.png)

This is a N:M relationship between EMPLOYEE and PROJECT because many employees work on different projects.



- (min-max) notation for relationship structural constraints:
  - This notation specifies that each entity participates in at least min and at most max relationship instances in a relationship.
  - $0\le min\le max$, $max\ge 1$

![min-max-notation](images/min-max-notation.png)



## 1.6 Recursive Relationship Type

- A recursive relationship is one in which the same entity participates more than once in the relationship. The relationship should be marked by the role that an entity takes in the participation.
- It is also called a self-referencing relationship type.
- Suppose one employee is assigned the task of supervising the other employees. The supervision relationship is a recursive relationship because the same entity, a particular employee, participates more than once in the relationship, as a supervisor and as a supervisee.



## 1.7 Weak Entity Types

- A weak entity that does not have a key attribute and is identification-dependent on another entity type. It must participate in identifying relationship type with an owner or identifying entity type. In other words, weak entity type must be owned by some owener entity type.
- A weak entity is identified by the combination of: (1) its partial key and (2) the identifying entity type related to the identifying relationship type.
- For example, the EMPLOYEE entity type owns the DEPENDENT entity type.



## 1.8 ER Diagrams

Notations

![er-notation](images/er-notation.png)
