#  SQL
1. Walkthrough on the Service Operations lifecycle 
2. Introduction to key production process focus areas
3. RDBMS overview covering the need for 2/3 tier architectures and databases as a central store for data
4. Tables, relationship, keys and normalization
5. SQL inserts, updates, select, delete and merge
6. SQL Query construct - simple select, where clause, order by, group by functions, some important SQL functions for Oracle
7. Data Modeling, types and Normalization basics
8. Other SQL concepts such as views, indexes, partitions
9. Exposure to tools such as SQL Developer
10. Database transactions and overview of ACID properties
11. Java exercise to cover basic CRUD operations using JDBC which demonstrate connectivity and basic transactions



## Database Architecture 

What is Database Architecture?
A Database Architecture is a representation of DBMS design. It helps to design, develop, implement, and maintain the database management system. A DBMS architecture allows dividing the database system into individual components that can be independently modified, changed, replaced, and altered. It also helps to understand the components of a database.


### Types of Database Architectures 
####Types of DBMS Architecture
* 1-Tier Architecture
* 2-Tier Architecture
* 3-Tier Architecture






1 Tier Architecture in DBMS is the simplest architecture of Database in which the client, server, and Database all reside on the same machine. A simple one tier architecture example would be anytime you install a Database in your system and access it to practice SQL queries. But such architecture is rarely used in production.

2-Tier Architecture A 2 Tier Architecture in DBMS is a Database architecture where the presentation layer runs on a client (PC, Mobile, Tablet, etc.), and data is stored on a server called the second tier. Two tier architecture provides added security to the DBMS as it is not exposed to the end-user directly. It also provides direct and faster communication.

3-Tier Architecture
A 3 Tier Architecture in DBMS is the most popular client server architecture in DBMS in which the development and maintenance of functional processes, logic, data access, data storage, and user interface is done independently as separate modules. Three Tier architecture contains a presentation layer, an application layer, and a database server.
3-Tier database Architecture design is an extension of the 2-tier client-server architecture. A 3-tier architecture has the following layers:
* Presentation layer (your PC, Tablet, Mobile, etc.)
* Application layer (server)
* Database Server
The goal of Three Tier client-server architecture is:
To separate the user applications and physical database
To support DBMS characteristics
Program-data independence
Supporting multiple views of the data


### What is a Table 
A database consists of one or more tables.  Each table is made up of rows and columns.  If you think of a table as a grid, the column go from left to right across the grid and each entry of data is listed down as a row.

Each row in a relational is uniquely  identified by a primary key.  This can be by one or more sets of column values.  In most scenarios it is a single column, such as employeeID.

Every relational table has one primary key.  Its purpose is to uniquely identify each row in the database.  No two rows can have the same primary key value.  The practical result of this is that you can select every single row by just knowing its primary key.


Columns are defined to hold a specific type of data, such as dates, numeric, or textual data.  In the simplest of definitions a column is defined by its name and data type.  The name is used in SQL statements when selecting and ordering data, and the data type is used to validate information stored.


Database Table Rows
A database table can contain zero or more rows.  When there are zero, it said to be empty.  There is not practical limit on the number of rows a table can hold; however, remember the table’s primary key may have some influence on this.

What I mean, is that if your table holds states, and the primary key is the state’s abbreviation, then by definition, since there are only fifty states in the union, and you can not have duplicates in a primary key, your table is limited to fifty rows.
Also, strictly speaking, in a relational database table there is no first or last row.  Yes, you can tease out a first row of a result using a keyword such as LIMIT or TOP, but those are used once the data is retrieved and sorted.  The difference here is that you’re seeing the first row of the result, not what is physically stored in the table.

### Relationships 
Relationships are meaningful associations between tables that contain related information — they’re what make databases useful. Without some connection between tables in a database, you may as well be working with disparate spreadsheet files rather than a database system.


* One-to-one relationship

  In a one-to-one relationship, a record in one table can correspond to only one record in another table (or in some cases, no records). One-to-one relationships aren’t the most common, since in many cases you can store corresponding information in the same table. Whether you split up that information into multiple tables depends on your overall data model and design methodology; if you’re keeping tables as narrowly-focused as possible (like in a normalized database), then you may find one-to-one relationships useful.
  
    Let’s say you’re organizing employee information at your company, and you also want to keep track of each employee’s computer. Since each employee only gets one computer and those computers are not shared between employees, you could add fields to your Employee table that hold information like the brand, year, and operating system of each computer. However, that can get messy from a semantic standpoint — does computer information really belong in a table about employees? That’s for you to decide, but another option is to create a Computers table with a one-to-one relationship to the Employee table
    Citizen - Passport
* One-to-many relationship
    
    One-to-many relationships are the most common type of relationships between tables in a database. In a one-to-many (sometimes called many-to-one) relationship, a record in one table corresponds to zero, one, or many records in another table.
    For example, think about tables for customers and their orders, like in Metabase’s Sample Database, where one record from the People table can be linked to many records in the Orders table. In this case, one customer can place many orders, and those multiple order records will all link back to a single record in the People table. That connection is codified through the User_ID field, which is a primary key in the People table and a foreign key in the Orders table.
    Department --> Employee is the prefect example
* Many-to-many relationship
    
    A many-to-many relationship indicates that multiple records in a table are linked to multiple records in another table. Those records may only be associated with a single record (or none at all) but the key is that they can and often are linked to more than one. Many-to-many relationships aren’t very common in practical database use cases, since adhering to normalization often involves breaking up many-to-many relationships into separate, more focused tables.
    E.g. Many Cars can be Sold by Many Dealers 
    or Many Dealers can sell many cars 

### Normalization 
Database Normalization is a technique of organizing the data in the database. Normalization is a systematic approach of decomposing tables to eliminate data redundancy(repetition) and undesirable characteristics like Insertion, Update and Deletion Anomalies. It is a multi-step process that puts data into tabular form, removing duplicated data from the relation tables.
Normalization is used for mainly two purposes,

Eliminating redundant(useless) data.
Ensuring data dependencies make sense i.e data is logically stored.
Problems Without Normalization
If a table is not properly normalized and have data redundancy then it will not only eat up extra memory space but will also make it difficult to handle and update the database, without facing data loss. Insertion, Updation and Deletion Anomalies are very frequent if database is not normalized. To understand these anomalies let us take an example of a Student table.

| Band Name         | 
|-------------------| 
| Seventh Wonder    | 
| Metallica         | 
| The Ocean         | 
| Within Temptation | 
| Death             | 
| Van Canto         | 
| Dream Theater     | 

| rollno  | name  |  branch | hod  |  office_tel |
|---|---|---|---|---|
|401| A |CS| Mr. X  | 12  |
|402| C |CS| Mr. X  | 12 |
|403| D |CS|Mr. X   | 12 |

In the table above, we have data of 4 Computer Sci. students. As we can see, data for the fields


#### Insertion Anomaly
Suppose for a new admission, until and unless a student opts for a branch, data of the student cannot be inserted, or else we will have to set the branch information as NULL.

Also, if we have to insert data of 100 students of same branch, then the branch information will be repeated for all those 100 students.

These scenarios are nothing but Insertion anomalies.


#### Updation Anomaly
What if Mr. X leaves the college? or is no longer the HOD of computer science department? In that case all the student records will have to be updated, and if by mistake we miss any record, it will lead to data inconsistency. This is Updation anomaly.


#### Deletion Anomaly
In our Student table, two different informations are kept together, Student information and Branch information. Hence, at the end of the academic year, if student records are deleted, we will also lose the branch information. This is Deletion anomaly.


#### Normalization Rule
##### Normalization rules are divided into the following normal forms:

1. First Normal Form
2. Second Normal Form
3. Third Normal Form
4. BCNF
5. Fourth Normal Form

First Normal Form (1NF)
For a table to be in the First Normal Form, it should follow the following 4 rules:

1. It should only have single(atomic) valued attributes/columns.
2. Values stored in a column should be of the same domain
3. All the columns in a table should have unique names.
4. And the order in which data is stored, does not matter.


##### Second Normal Form (2NF)
For a table to be in the Second Normal Form,

1. It should be in the First Normal form.
2. And, it should not have Partial Dependency.
To understand what is Partial Dependency and how to normalize a table to 2nd normal for,


##### Third Normal Form (3NF)
A table is said to be in the Third Normal Form when,

1. It is in the Second Normal form.
2. And, it doesn't have Transitive Dependency.

##### Boyce and Codd Normal Form (BCNF)
Boyce and Codd Normal Form is a higher version of the Third Normal form. This form deals with certain type of anomaly that is not handled by 3NF. A 3NF table which does not have multiple overlapping candidate keys is said to be in BCNF. For a table to be in BCNF, following conditions must be satisfied:

1. R must be in 3rd Normal Form
2. and, for each functional dependency ( X → Y ), X should be a super Key.


##### Fourth Normal Form (4NF)
A table is said to be in the Fourth Normal Form when,

1. It is in the Boyce-Codd Normal Form.
2. And, it doesn't have Multi-Valued Dependency.


## Setup
First drop your existing database that was created in the tutorial. `DROP DATABASE record_company;`

Copy the code inside the [schema.sql](schema.sql) file, paste it into MySQL Workbench, and run it. (This file contains the code necessary to create and add the tables from the tutorial video)

## SQL inserts, updates, select, delete and merge
#  Exercise 1. Create a Songs Table
[Solution](code/1.sql)

This table should be called `songs` and have four properties with these exact names.
1. `id`: An integer that is the primary key, and auto increments.
2. `name`: A string that cannot be null.
3. `length`: A float that represents the length of the song in minutes that cannot be null.
4. `album_id`: An integer that is a foreign key referencing the albums table that cannot be null.

After successfully creating the table copy the code from [data.sql](data.sql) into MySQL Workbench, and run it to populate all of the data for the rest of the exercises. If you do not encounter any errors, then your answer is most likely correct.

# 2. Exercise Select only the Names of all the Bands
[Solution](code/2.sql)

Change the name of the column the data returns to `Band Name`

| Band Name         | 
|-------------------| 
| Seventh Wonder    | 
| Metallica         | 
| The Ocean         | 
| Within Temptation | 
| Death             | 
| Van Canto         | 
| Dream Theater     | 

# 3. Exercise Select the Oldest Album
[Solution](code/3.sql)

Make sure to only return one result from this query, and that you are not returning any albums that do not have a release year.

| id | name                   | release_year | band_id | 
|----|------------------------|--------------|---------| 
| 5  | ...And Justice for All | 1988         | 2       | 

# 4. Exercise Get all Bands that have Albums
[Solution](code/4.sql)

There are multiple different ways to solve this problem, but they will all involve a join.

Return the band name as `Band Name`.

| Band Name         | 
|-------------------| 
| Seventh Wonder    | 
| Metallica         | 
| The Ocean         | 
| Within Temptation | 
| Death             | 
| Van Canto         | 

# 5. Exercise Get all Bands that have No Albums
[Solution](code/5.sql)

This is very similar to #4 but will require more than just a join.

Return the band name as `Band Name`.

| Band Name     | 
|---------------| 
| Dream Theater | 

# 6. Exercise Get the Longest Album
[Solution](code/6.sql)

This problem sounds a lot like #3 but the solution is quite a bit different. I would recommend looking up the SUM aggregate function.

Return the album name as `Name`, the album release year as `Release Year`, and the album length as `Duration`.

| Name           | Release Year | Duration          | 
|----------------|--------------|-------------------| 
| Death Magnetic | 2008         | 74.76666593551636 | 

# 7. Exercise Update the Release Year of the Album with no Release Year
[Solution](code/7.sql)

Set the release year to 1986.

You may run into an error if you try to update the release year by using `release_year IS NULL` in the WHERE statement of your UPDATE. This is because MySQL Workbench by default will not let you update a table that has a primary key without using the primary key in the UPDATE statement. This is a good thing since you almost never want to update rows without using the primary key, so to get around this error make sure to use the primary key of the row you want to update in the WHERE of the UPDATE statement.

# 8. Exercise Insert a record for your favorite Band and one of their Albums
[Solution](code/8.sql)

If you performed this correctly you should be able to now see that band and album in your tables.

# 9. Exercise Exercise Delete the Band and Album you added in #8
[Solution](code/9.sql)

The order of how you delete the records is important since album has a foreign key to band.

# 10. Exercise Get the Average Length of all Songs
[Solution](code/10.sql)

Return the average length as `Average Song Duration`.

| Average Song Duration | 
|-----------------------| 
| 5.352472513259112     | 


#  Exercise 11. Select the longest Song off each Album
[Solution](code/11.sql)

Return the album name as `Album`, the album release year as `Release Year`, and the longest song length as `Duration`.

| Album                       | Release Year | Duration | 
|-----------------------------|--------------|----------| 
| Tiara                       | 2018         | 9.5      | 
| The Great Escape            | 2010         | 30.2333  | 
| Mercy Falls                 | 2008         | 9.48333  | 
| Master of Puppets           | 1986         | 8.58333  | 
| ...And Justice for All      | 1988         | 9.81667  | 
| Death Magnetic              | 2008         | 9.96667  | 
| Heliocentric                | 2010         | 7.48333  | 
| Pelagial                    | 2013         | 9.28333  | 
| Anthropocentric             | 2010         | 9.4      | 
| Resist                      | 2018         | 5.85     | 
| The Unforgiving             | 2011         | 5.66667  | 
| Enter                       | 1997         | 7.25     | 
| The Sound of Perseverance   | 1998         | 8.43333  | 
| Individual Thought Patterns | 1993         | 4.81667  | 
| Human                       | 1991         | 4.65     | 
| A Storm to Come             | 2006         | 5.21667  | 
| Break the Silence           | 2011         | 6.15     | 
| Tribe of Force              | 2010         | 8.38333  | 

# Exercise 12. Get the number of Songs for each Band
[Solution](code/12.sql)

This is one of the toughest question on the list. It will require you to chain together two joins instead of just one.

Return the band name as `Band`, the number of songs as `Number of Songs`.

| Band              | Number of Songs | 
|-------------------|-----------------| 
| Seventh Wonder    | 35              | 
| Metallica         | 27              | 
| The Ocean         | 31              | 
| Within Temptation | 30              | 
| Death             | 27              | 
| Van Canto         | 32              | 



# Reading Material 

# Relational databases fundamentals

In this repository you will find short overview about key concepts about relational databases.

# Table of Contents

- [Relational model](#relational-model)
    * [Key Concepts](#key-concepts)
    * [Advantages of relational databases](#advantages-of-relational-databases)
    * [Disadvantages of relational databases](#disadvantages-of-relational-databases)
- [Relational algebra](#relational-algebra)
    * [Basic Relational algebra operations](#basic-relational-algebra-operations)
    * [Extended Relational algebra operations](#extended-relational-algebra-operations)
- [Structured Query Language](#structured-query-language-sql)
- [SQL examples](#sql-examples)
    * [Basic select](#basic-select)
    * [Table Variables and Set Operators](#table-variables-and-set-operators)
    * [Subqueries](#subqueries)
    * [Aggregation functions](#aggregation-functions)
    * [Join Operators](#join-operators)
- [Database normalization](#database-normalization)
    * [Anomalies](#anomalies)
    * [Functional dependency](#functional-dependency)
    * [Normalization of relations. Normal forms](#normalization-of-relations-normal-forms)
- [Transactions](#transactions)
    * [ACID](#acid)
    * [Transaction phenomenas/problems](#transaction-phenomenasproblems)
    * [Isolation levels](#isolation-levels)
- [Indexes](#indexes)
    * [How Indexes Work](#how-indexes-work)
    * [Composit index](#composit-index)
    * [Clustered & Non-Clustered Indexes](#clustered--non-clustered-indexes)
    * [Advantages/Disadvantages of using indexes](#advantagesdisadvantages-of-using-indexes)
    * [Implementation](#implementation)
- [SQL Constraints](#sql-constraints)
- [Triggers](#triggers)
    * [Trigger structure](#trigger-structure)
    * [Triggers examples](#triggers-examples)
- [Views](#views)
    * [Read-only/updatable views](#read-onlyupdatable-views)
    * [SQL for dealing with views](#sql-for-dealing-with-views)
    * [Materialized view](#materialized-view)
- [Stored procedures](#stored-procedures)
    * [SP Advantages](#sp-advantages)
    * [SP Disadvantages](#sp-disadvantages)
- [Scalability](#scalability)
    * [Vertical Database Scalability](#vertical-database-scalability)
    * [Horizontal Database Scalability](#horizontal-database-scalability)
    * [Partition](#partition)
    * [Replication](#replication)
    * [Sharding](#sharding)
    

# Relational model

The relational model for database management is an approach to managing data using a structure and language consistent with first-order predicate logic, first described in 1969 by Edgar F. Codd, where all data is represented in terms of tuples, grouped into relations. A database organized in terms of the relational model is a relational database.

The purpose of the relational model is to provide a declarative method for specifying data and queries: users directly state what information the database contains and what information they want from it, and let the database management system software take care of describing data structures for storing the data and retrieval procedures for answering queries.

Most relational databases use the SQL data definition and query language; these systems implement what can be regarded as an engineering approximation to the relational model. A table in an SQL database schema corresponds to a predicate variable; the contents of a table to a relation; key constraints, other constraints, and SQL queries correspond to predicates. However, SQL databases deviate from the relational model in many details, and Codd fiercely argued against deviations that compromise the original principles. In relational data model the data is organized into tables. These tables are called relations.

## Key Concepts  

* **Schema** - structural description of relations in database.
* **Instance** - actual contents at given point in time.
* **Database** - set of named relations (or tables).
* Each relation has a set of named **attributes** (or **columns**)
* Each **tuple** (or **row**) has a value for each attribute
* Each attribute has a **type** (or **domain**)
* **NULL** – special value for “unknown” or “undefined”
* Key – attribute whose value is unique in each tuple. Or set of attributes whose combined values are unique

![relational-model](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/relational_model.png)

## Advantages of relational databases

* **Query flexibility.** As long as your schema is normalized, you don’t have to know up front how you will query your data. You can always gather together the data you want using joins, views, filter and indexes.
* **Consistency via ACID transactions.** The relational database ensures that your commits are always atomic, consistent, isolated and durable. If an error occurrs, the whole transaction can be rolled back, restoring a consistent state. This is critical in some domains (e.g. banking).
* **Safety due to defined schema and strict constraint checks** (e.g. column types, uniqueness constraints, referential integrity). Your data has a fixed structure you can rely on. You cannot accidentally misspell a column name, submit a string instead of an integer or enter a non-existing foreign key. The relational database will refuse the query and tell you. This is very comfortable. However, data validation and constraint checking can also (and often must) be done in the application or user interface layer. Validating data only in the database is often too late. Usually the user’s input has to be checked at a upstream layer anyway. Moreover, complex business validation cannot be done by the database. Hence, it is questionable if a redundant check done by the database is really necessary (extra maintenance effort and performance hit).
* **Maturity.** 45+ years of industry experience leading to mature databases, tools, driver, programming libraries, ORM. Knowledge of RDBMS is a basic skill every software developer has.
* **Huge toolkit** (trigger, stored procedures, advanced indexes, views) available.

## Disadvantages of relational databases

* Impedance mismatch between the object-oriented and the relational world.
* The relational data model doesn’t fit in with every domain.
* Difficult schema evolution due to an inflexible data model.
* Weak distributed availability due to poor horizontal scalability.
* Performance hit due to joins, ACID transactions and strict consistency constraints (especially in distributed environments).

[Great article about pros and cons of relational databases](https://blog.philipphauer.de/relational-databases-strength-weaknesses-mongodb/)


# Relational algebra

Relational algebra, first created by Edgar F. Codd while at IBM, is a family of algebras with a well-founded semantics used for modelling the data stored in relational databases, and defining queries on it.

The main application of relational algebra is providing a theoretical foundation for relational databases, particularly query languages for such databases, chief among which is SQL.

## Basic Relational algebra operations

For understanding it is important to remember that the **result of any operation of algebra over relations is another relationship**, which can then also be used in other operations.

**Selection (σ)** 

Selection operator is used to select tuples (rows) from a relation based on some condition. 

```
σ (Cond)(Relation Name)
```

Extract students whose age is greater than 18 from STUDENT relation

```
σ (AGE>18)(STUDENT)
```

**Projection (∏)**

A projection is an operation where only attributes from the specified domains are selected from the relation, that is, only the necessary columns are selected from the table, and if several identical tuples are obtained, then in the resulting relation there is only one copy of such a tuple.

```
∏(Column 1,Column 2….Column n)(Relation Name)
```

Extract ID and NAME columns from STUDENT relation

```
∏(ID,NAME)(STUDENT)
```

**Cross Product (X)**

Cross product (Cartesian Product) is used to join two relations. For every row of Relation1, each row of Relation2 is concatenated. If Relation1 has m tuples and and Relation2 has n tuples, cross product of Relation1 and Relation2 will have m X n tuples.

```
Relation1 X Relation2
```

**Union (U)** 

Union on two relations R1 and R2 can only be computed if R1 and R2 are union compatible (These two relation should have same number of attributes and corresponding attributes in two relations have same domain) . Union operator when applied on two relations R1 and R2 will give a relation with tuples which are either in R1 or in R2. The tuples which are in both R1 and R2 will appear only once in result relation.

```
Relation1 U Relation2
```

**Minus (-)**

Minus on two relations R1 and R2 can only be computed if R1 and R2 are union compatible. Minus operator when applied on two relations as R1-R2 will give a relation with tuples which are in R1 but not in R2.

```
Relation1 - Relation2
```

**Rename (ρ)**
 
Rename operator is used to give another name to a relation. To rename STUDENT relation to STUDENT1, we can use rename operator like:

```
ρ(STUDENT1, STUDENT)
```

## Extended Relational algebra operations

Extended operators are those operators which can be derived from basic operators.There are mainly three types of extended operators in Relational Algebra:

* Join
* Intersection
* Divide 

**Intersection (∩)** 

Intersection on two relations R1 and R2 can only be computed if R1 and R2 are union compatible (These two relation should have same number of attributes and corresponding attributes in two relations have same domain). Intersection operator when applied on two relations as R1∩R2 will give a relation with tuples which are in R1 as well as R2

```
Example: Find a person who is student as well as employee -  STUDENT ∩ EMPLOYE
```

**Conditional Join (⋈c)** 

Conditional Join is used when you want to join two or more relation based on some conditions. Example: Select students whose ROLL_NO is greater than EMP_NO of employees

**Equijoin (⋈)**
 
Equijoin is a special case of conditional join where only equality condition holds between a pair of attributes. As values of two attributes will be equal in result of equijoin, only one attribute will be appeared in result.

**Natural Join (⋈)**
 
It is a special case of equijoin in which equality condition hold on all attributes which have same name in relations R and S (relations on which join operation is applied). While applying natural join on two relations, there is no need to write equality condition explicitly. Natural Join will also return the similar attributes only once as their value will be same in resulting relation.

Example: Select students whose ROLL_NO is equal to ROLL_NO of STUDENT_SPORTS 

Natural Join is by default inner join because the tuples which does not satisfy the conditions of join does not appear in result set. e.g.; The tuple having ROLL_NO 3 in STUDENT does not match with any tuple in STUDENT_SPORTS, so it has not been a part of result set.

**Left Outer Join (⟕)** 

When applying join on two relations R and S, some tuples of R or S does not appear in result set which does not satisfy the join conditions. But Left Outer Joins gives all tuples of R in the result set. The tuples of R which do not satisfy join condition will have values as NULL for attributes of S.

**Right Outer Join (⟖)**

When applying join on two relations R and S, some tuples of R or S does not appear in result set which does not satisfy the join conditions. But Right Outer Joins gives all tuples of S in the result set. The tuples of S which do not satisfy join condition will have values as NULL for attributes of R.

**Full Outer Join (⟗)** 

When applying join on two relations R and S, some tuples of R or S does not appear in result set which does not satisfy the join conditions. But Full Outer Joins gives all tuples of S and all tuples of R in the result set. The tuples of S which do not satisfy join condition will have values as NULL for attributes of R and vice versa.

**Division Operator (÷)** 

Division operator A÷B can be applied if and only if:

* Attributes of B is proper subset of Attributes of A.
* The relation returned by division operator will have attributes = (All attributes of A – All Attributes of B)
* The relation returned by division operator will return those tuples from relation A which are associated to every B’s tuple.

![sql](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/sql.jpg)

# Structured Query Language (SQL)

Structured Query Language is a standard Database language which is used to create, maintain and retrieve the relational database.

All SQL commands could be separated as Data Definition Language, Data Manipulation Language, Transaction Control Language and Data Control Language.

![sql](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/sql-commands.jpg)


**Data Definition Language (DDL)** is used to define database structure or schema. DDL is also used to specify additional properties of the data. The storage structure and access methods used by the database system by a set of statements in a special type of DDL called a data storage and definition language. These statements defines the implementation details of the database schema, which are usually hidden from the users. The data values stored in the database must satisfy certain consistency constraints.

```
CREATE : to create objects in database
ALTER : alters the structure of database
DROP : delete objects from database
RENAME : rename an objects
```

**Data Manipulation Language (DML)**  used for managing data with in schema objects

```
SELECT : retrieve data from the database
INSERT : insert data into a table
UPDATE : update existing data within a table
DELETE : deletes all records from a table , space for the records remain
```

**Transaction Control Language (TCL)** commands are used to manage transactions in database. These are used to manage the changes made by DML-statements. It also allows statements to be grouped together into logical transactions.

```
COMMIT :    Commit command is used to permanently save any transaction
            into database.
ROLLBACK :  This command restores the database to last committed state.
            It is also use with savepoint command to jump to a savepoint
            in a transaction.
SAVEPOINT : Savepoint command is used to temporarily save a transaction so
            that you can rollback to that point whenever necessary.
```

**Data Control Language (DCL)** is a syntax similar to a computer programming language used to control access to data stored in a database (Authorization). In particular, it is a component of Structured Query Language (SQL).

```
GRANT : allow specified users to perform specified tasks.
REVOKE : cancel previously granted or denied permissions.
```

# SQL examples

For all examples I will use next database which consists of 3 tables:

```
College(cName,state,enrollment) 
Student(sID,sName,GPA,sizeHS)
Apply(sID,cName,major,decision)
```

We have the college relation: college relation contains information about the name of the colleges, the state, and the enrollment of those colleges.
We have the student relation, which contains student IDs, their names,their GPA, and the size of the high school that they come from.
And finally, the application information, that tells us that a particular student applied to a particular college for a particular major and there was a decision of that application

![sql](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/db-str.png)

## Basic select

IDs, names, and GPAs of students with GPA > 3.6:

```
select sID, sName, GPA
from Student
where GPA > 3.6;
```

Student names and majors for which they've applied - output will contains duplicates:

```
select sName, major
from Student, Apply
where Student.sID = Apply.sID;
```

Same query with **distinct** statement for removing duplicates:

```
select distinct sName, major
from Student, Apply
where Student.sID = Apply.sID;
```

Names and GPAs of students with sizeHS < 1000 applying to CS at Stanford, and the application decision:

```
select sname, GPA, decision
from Student, Apply
where Student.sID = Apply.sID
  and sizeHS < 1000 and major = 'CS' and cname = 'Stanford';
```

All large campuses with CS applicants - using name of relations for solving ambiguous column names:

```
select distinct College.cName
from College, Apply
where College.cName = Apply.cName
  and enrollment > 20000 and major = 'CS';
```

Application information (cross product for all three relations):

```
select Student.sID, sName, GPA, Apply.cName, enrollment
from Student, College, Apply
where Apply.sID = Student.sID and Apply.cName = College.cName;

```

Sort by decreasing GPA - using **order by** keyword and specifying descening order (**desc**):

```
select Student.sID, sName, GPA, Apply.cName, enrollment
from Student, College, Apply
where Apply.sID = Student.sID and Apply.cName = College.cName
order by GPA desc;
```

We could have several sorting in one querry:

```
select Student.sID, sName, GPA, Apply.cName, enrollment
from Student, College, Apply
where Apply.sID = Student.sID and Apply.cName = College.cName
order by GPA desc, enrollment;
```

Using **like** predicate - querry will return such majors like biology, marin biology, etc : 

```
select sID, major
from Apply
where major like '%bio%';

```

Add scaled GPA based on sizeHS:

```
select sID, sName, GPA, sizeHS, GPA*(sizeHS/1000.0)
from Student;
```

Rename result attribute (using **as**):

```
select sID, sName, GPA, sizeHS, GPA*(sizeHS/1000.0) as scaledGPA
from Student;
```

## Table Variables and Set Operators

Application information using table variables for increasing readability:

```
select S.sID, S.sName, S.GPA, A.cName, C.enrollment
from Student S, College C, Apply A
where A.sID = S.sID and A.cName = C.cName;
```

Pairs of students with same GPA without self-pairings and reverse-pairings:

```
select S1.sID, S1.sName, S1.GPA, S2.sID, S2.sName, S2.GPA
from Student S1, Student S2
where S1.GPA = S2.GPA and S1.sID < S2.sID;
```

List of college names and student names - using **union** operator (without duplicates, **union all** will leave duplicates):

```
select cName as name from College
union
select sName as name from Student;
```

IDs of students who applied to both CS and EE - using **intersection** operator:

```
select sID from Apply where major = 'CS'
intersect
select sID from Apply where major = 'EE';
```

IDs of students who applied to CS but not EE - using **except** operator:

```
select sID from Apply where major = 'CS'
except
select sID from Apply where major = 'EE';
```


## Subqueries

Sub-queries are nested, select statements within the condition.

IDs and names of students applying to CS:

```
select sID, sName
from Student
where sID in (select sID from Apply where major = 'CS');
```

Students who applied to CS but not EE (query we used 'Except' for earlier):

```
select sID, sName
from Student
where sID in (select sID from Apply where major = 'CS')
  and sID not in (select sID from Apply where major = 'EE');
```

Colleges such that some other college is in the same state (like Berkeley and Stanford in the same state):

```
select cName, state
from College C1
where exists (select * from College C2
              where C2.state = C1.state and C2.cName <> C1.cName);
```

Higher GPA than all other students:

```
select sName, GPA
from Student
where GPA >= all (select GPA from Student);
```

Students whose scaled GPA changes GPA by more than 1:

```
select *
from (select sID, sName, GPA, GPA*(sizeHS/1000.0) as scaledGPA
      from Student) G
where abs(scaledGPA - GPA) > 1.0;
```

## Aggregation functions

These are functions that will appear in the select clause initially and what they do is they perform computations over sets of values in multiple rows of our relations, and the basic aggregation functions supported by every SQL system are minimum, maximum, some, average and count.

Now once we've introduced the aggregation functions we can also add two new clasues to the SQL select from where statement, the **group by** and **having** clause.

The group by allows us to partition our relations into groups and then will compute aggregated aggregate functions over each group independently.
The having condition allows us to test filters on the results of aggregate values. The where condition applies to single rows at a time. The having condition will apply to the groups that we generate from the group by clause.


Average GPA of all students:

```
select avg(GPA)
from Student;
```

Lowest GPA of students applying to CS:

```
select min(GPA)
from Student, Apply
where Student.sID = Apply.sID and major = 'CS';
```

Number of colleges bigger than 15,000:

```
select count(*)
from College
where enrollment > 15000;
```

Number of applications to each college:

```
select cName, count(*)
from Apply
group by cName;
```

College enrollments by state:

```
select state, sum(enrollment)
from College
group by state;
```

Minimum + maximum GPAs of applicants to each college & major:

```
select cName, major, min(GPA), max(GPA)
from Student, Apply
where Student.sID = Apply.sID
group by cName, major;
```

Colleges with fewer than 5 applications:

```
select cName
from Apply
group by cName
having count(sID) < 5;
```

Majors whose applicant's maximum GPA is below the average:

```
select major
from Student, Apply
where Student.sID = Apply.sID
group by major
having max(GPA) < (select avg(GPA) from Student);
```

## Join Operators

Student names and majors for which they've applied

```
select distinct sName, major
from Student inner join Apply
on Student.sID = Apply.sID;
```

**Inner join** could be simplified to just **join**

```
select distinct sName, major
from Student join Apply
on Student.sID = Apply.sID;
```

Names and GPAs of students with sizeHS < 1000 applying to CS at Stanford

```
select sName, GPA
from Student join Apply
on Student.sID = Apply.sID
where sizeHS < 1000 and major = 'CS' and cName = 'Stanford';
```

THREE-WAY INNER JOIN - application info: ID, name, GPA, college name, enrollment

```
select Apply.sID, sName, GPA, Apply.cName, enrollment
from (Apply join Student on Apply.sID = Student.sID) join College on Apply.cName = College.cName;
```

NATURAL JOIN - student names and majors for which they've applied

```
select distinct sName, major
from Student natural join Apply;
```

NATURAL JOIN WITH ADDITIONAL CONDITIONS - Names and GPAs of students with sizeHS < 1000 applying to CS at Stanford

```
select sName, GPA
from Student natural join Apply
where sizeHS < 1000 and major = 'CS' and cName = 'Stanford';
```

USING clause considered safer 

```
select sName, GPA
from Student join Apply using(sID)
where sizeHS < 1000 and major = 'CS' and cName = 'Stanford';
```

SELF-JOIN - Pairs of students with same GPA

```
select S1.sID, S1.sName, S1.GPA, S2.sID, S2.sName, S2.GPA
from Student S1 join Student S2 using(GPA)
where S1.sID < S2.sID;
```

LEFT OUTER JOIN - student application info: name, ID, college name, major and Include students who haven't applied anywhere

```
select sName, sID, cName, major
from Student left outer join Apply using(sID);

select sName, sID, cName, major
from Student left join Apply using(sID);

select sName, sID, cName, major
from Student natural left outer join Apply;
```

RIGHT OUTER JOIN - student application info: name, ID, college name, major. Include applications without matching students

```
select sName, sID, cName, major
from Student natural right outer join Apply;
```

FULL OUTER JOIN - Student application info .Include students who haven't applied anywhere and applications without matching students

```
select sName, sID, cName, major
from Student full outer join Apply using(sID);
```

# Database normalization

Normalization is the process of splitting relations into well structured relations that allow users to insert, delete, and update tuples without introducing database inconsistencies. Without normalization many problems can occur when trying to load an integrated conceptual model into the DBMS. These problems arise from relations that are generated directly from user views are called anomalies. There are three types of anomalies: update, deletion and insertion anomalies.

## Anomalies

Relation which are using for anomalies examples

![sql](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/anomalies.png)

An **update anomaly** is a data inconsistency that results from data redundancy and a partial update. For example, each employee in a company has a department associated with them as well as the student group they participate in. 
If A. Bruchs’ department is an error it must be updated at least 2 times or there will be inconsistent data in the database. If the user performing the update does not realize the data is stored redundantly the update will not be done properly.

A **deletion anomaly** is the unintended loss of data due to deletion of other data. For example, if the student group Beta Alpha Psi disbanded and was deleted from the table above, J. Longfellow and the Accounting department would cease to exist. This results in database inconsistencies and is an example of how combining information that does not really belong together into one table can cause problems.

An **insertion anomaly** is the inability to add data to the database due to absence of other data. For example, assume Student_Group is defined so that null values are not allowed. If a new employee is hired but not immediately assigned to a Student_Group then this employee could not be entered into the database. This results in database inconsistencies due to omission.

Update, deletion, and insertion anomalies are very undesirable in any database. Anomalies are avoided by the process of normalization.

## Functional dependency

Functional Dependency is a constraint between two sets of attributes in a relation from a database. Functional dependency is denoted by arrow (→). If an attributed A functionally determines B, then it is written as A → B.

For example employee_id → name means employee_id functionally determines name of employee. As another example in a time table database, {student_id, time} → {lecture_room}, student ID and time determine the lecture room where student should be.

A function dependency A → B mean for all instances of a particular value of A, there is same value of B.

For example in the below table A → B is true, but B → A is not true as there are different values of A for B = 3.

```
A   B
-----
1   3
2   3
4   0
1   3
4   0
```

**Trivial Functional Dependency**

X –> Y is trivial only when Y is subset of X.

```
ABC --> AB
ABC --> A
ABC --> ABC
```

X –> Y is a **non trivial functional dependencies** when Y is not a subset of X.

X –> Y is called completely non-trivial when X intersect Y is NULL.

```
Id --> Name, 
Name --> DOB
```

## Normalization of relations. Normal forms
 
The process of designing a database using the NF method is iterative and consists in the sequential transformation of the relation from 1NF to NF of a higher order according to certain rules. 

Each next NF is limited to a certain type of functional dependencies and elimination of corresponding anomalies when performing operations on database relations, as well as preserving the properties of previous NFs

### 1 NF

If a relation contain composite or multi-valued attribute, it violates first normal form or a relation is in first normal form if it does not contain any composite or multi-valued attribute. A relation is in first normal form if every attribute in that relation is singled valued attribute.

Relation STUDENT in table 1 is not in 1NF because of multi-valued attribute STUD_PHONE. Its decomposition into 1NF has been shown in table 2.

![nf1](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/nf1.png)

### 2 NF

To be in second normal form, a relation must be in first normal form and relation must not contain any partial dependency. A relation is in 2NF iff it has No Partial Dependency, i.e., no non-prime attribute (attributes which are not part of any candidate key) is dependent on any proper subset of any candidate key of the table.

![nf2](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/nf2.png)

Partial Dependency – If proper subset of candidate key determines non-prime attribute, it is called partial dependency.

Example 1 – In relation STUDENT_COURSE given in Table 3,

```
FD set: {COURSE_NO->COURSE_NAME}
Candidate Key: {STUD_NO, COURSE_NO}
```

In FD COURSE_NO->COURSE_NAME, COURSE_NO (proper subset of candidate key) is determining COURSE_NAME (non-prime attribute). Hence, it is partial dependency and relation is not in second normal form.

To convert it to second normal form, we will decompose the relation STUDENT_COURSE (STUD_NO, COURSE_NO, COURSE_NAME) as :

```
STUDENT_COURSE (STUD_NO, COURSE_NO)
COURSE (COURSE_NO, COURSE_NAME)
```

### 3 NF

The relation is in 3NF when it is in 2NF and each non-key attribute is not reliantly (non trasitively) dependent on the primary key. Simply put, the second rule requires you to move all non-key fields whose contents can relate to several table entries in separate tables.

# Transactions

A transaction is a single logical unit of work which accesses and possibly modifies the contents of a database. Transactions access data using read and write operations.

In order to maintain consistency in a database, before and after transaction, certain properties are followed. These are called **ACID properties**.

The ACID properties, in totality, provide a mechanism to ensure correctness and consistency of a database in a way such that each transaction is a group of operations that acts a single unit, produces consistent results, acts in isolation from other operations and updates that it makes are durably stored.

## ACID

**Atomicity**

This property means that either the entire transaction takes place at once or doesn’t happen at all. There is no midway i.e. transactions do not occur partially. Each transaction is considered as one unit and either runs to completion or is not executed at all. It involves following two operations.

* Abort: If a transaction aborts, changes made to database are not visible.
* Commit: If a transaction commits, changes made are visible.

Atomicity is also known as the **‘All or nothing rule’**.

**Consistency**

Consistency in database systems refers to the requirement that any given database transaction must change affected data only in allowed ways. Any data written to the database must be valid according to all defined rules, including constraints, cascades, triggers, and any combination thereof.

This means that integrity constraints must be maintained so that the database is consistent before and after the transaction. It refers to correctness of a database. 

**Isolation**

This property ensures that multiple transactions can occur concurrently without leading to inconsistency of database state. Transactions occur independently without interference. Changes occurring in a particular transaction will not be visible to any other transaction until that particular change in that transaction is written to memory or has been committed. This property ensures that the execution of transactions concurrently will result in a state that is equivalent to a state achieved these were executed serially in some order.

**Durability**

In database systems, durability is the ACID property which guarantees that transactions that have committed will survive permanently. For example, if a flight booking reports that a seat has successfully been booked, then the seat will remain booked even if the system crashes.

Durability can be achieved by flushing the transaction's log records to non-volatile storage before acknowledging commitment.

In distributed transactions, all participating servers must coordinate before commit can be acknowledged. This is usually done by a two-phase commit protocol.

Many DBMSs implement durability by writing transactions into a transaction log that can be reprocessed to recreate the system state right before any later failure. A transaction is deemed committed only after it is entered in the log.

## Transaction phenomenas/problems

There are 4 phenomenas/problems

* Lost update
* Dirty read
* Non-repeatebale read
* Phantom read

### Lost update

If two transactions are updating different columns of the same row, then there is no conflict. The second update blocks until the first transaction is committed and the final result reflects both update changes.

If the two transactions want to change the same columns, the second transaction will overwrite the first one, therefore losing the first transaction update.

So an update is lost when a user overrides the current database state without realizing that someone else changed it between the moment of data loading and the moment the update occurs.

![lost](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/lost.png)

### Dirty read

A dirty read occurs when a transaction reads data that has not yet been committed. For example, suppose transaction 1 updates a row. Transaction 2 reads the updated row before transaction 1 commits the update. If transaction 1 rolls back the change, transaction 2 will have read data that is considered never to have existed.

![lost](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/dirty.png)

### Non-repeatable reads

A nonrepeatable read occurs when a transaction reads the same row twice but gets different data each time. For example, suppose transaction 1 reads a row. Transaction 2 updates or deletes that row and commits the update or delete. If transaction 1 rereads the row, it retrieves different row values or discovers that the row has been deleted.

![lost](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/non-rep.png)

### Phantom read

A phantom is a row that matches the search criteria but is not initially seen. For example, suppose transaction 1 reads a set of rows that satisfy some search criteria. Transaction 2 generates a new row (through either an update or an insert) that matches the search criteria for transaction 1. If transaction 1 reexecutes the statement that reads the rows, it gets a different set of rows.

![lost](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/phantom.png)

## Isolation levels

Most DBMSs offer a number of transaction isolation levels, which control the degree of locking that occurs when selecting data. For many database applications, the majority of database transactions can be constructed to avoid requiring high isolation levels (e.g. SERIALIZABLE level), thus reducing the locking overhead for the system. The programmer must carefully analyze database access code to ensure that any relaxation of isolation does not cause software bugs that are difficult to find. Conversely, if higher isolation levels are used, the possibility of deadlock is increased, which also requires careful analysis and programming techniques to avoid.

The isolation levels defined by the ANSI/ISO SQL standard are listed as follows.

### Read uncommitted

This is the lowest isolation level. In this level, dirty reads are allowed, so one transaction may see not-yet-committed changes made by other transactions.

### Read committed

In this isolation level, a lock-based concurrency control DBMS implementation keeps write locks (acquired on selected data) until the end of the transaction, but read locks are released as soon as the SELECT operation is performed (so the non-repeatable reads phenomenon can occur in this isolation level).

Putting it in simpler words, read committed is an isolation level that guarantees that any data read is committed at the moment it is read. It simply restricts the reader from seeing any intermediate, uncommitted, 'dirty' read. It makes no promise whatsoever that if the transaction re-issues the read, it will find the same data; data is free to change after it is read.

### Repeatable read

In this isolation level, a lock-based concurrency control DBMS implementation keeps read and write locks (acquired on selected data) until the end of the transaction.

Write skew is possible at this isolation level, a phenomenon where two writes are allowed to the same column(s) in a table by two different writers (who have previously read the columns they are updating), resulting in the column having data that is a mix of the two transactions.

### Serializable

This is the highest isolation level.

With a lock-based concurrency control DBMS implementation, serializability requires read and write locks (acquired on selected data) to be released at the end of the transaction. Also range-locks must be acquired when a SELECT query uses a ranged WHERE clause, especially to avoid the phantom reads phenomenon.

When using non-lock based concurrency control, no locks are acquired; however, if the system detects a write collision among several concurrent transactions, only one of them is allowed to commit. See snapshot isolation for more details on this topic.

![lost](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/isolation.png)

# Indexes

An index is a data structure that optimize searching and accessing the data. It’s like an index at the back of a book. When your database start to grow, the performance will be a concern. Hence, getting directly to a specific row in a large table in the least possible time is a priority.

One of the ways that will optimize your database searching and accessing is having indexes on the columns that you usually access the table using it.

What the DBMS will do when you ask for a specific row, it will go sequentially and check with every row; “Is this the row that I need?”, If yes return it, if no, keep searching till the end.

But, we have a better way to do that. An index, as we’ve mentioned, is a data structure, it won’t be obvious for you, but it’s stored inside the DBMS, most commonly as a B, B+ trees or hash tables.

**By default, Most of the DBMS automatically create an index on primary and unique columns.**

## How Indexes Work

Let’s say that you have an index for a primary key. This will create an ordered list of primary key values in a separate table, each entry has a pointer points to the relative value in the original table.

So, whenever you want to access a table using the primary key, it will use binary search algorithm (takes time of O(LogN)) to access the required value in the Index table, and then, go to the relative value in the original table.

![index](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/index.png)

And, definitely, you can create another index on another column, even if it’s a non-primary column, like first name, assuming that you usually access the table using that column.

The decision for choosing another column (besides the primary key) to be indexed-ed can be delayed until the database has been used for a while. This is because we want to know how users are really using our database, and what kind of queries they’re running rather than how we hoped or thought.

## Composit index

You can also create an index on a combination of columns, meaning if you often access the table using the first name, and last name, you can create an index on both, the first name and last name.

Now, the Index table will be sorted according to the first name, and for each value of the first name it will be sorted according to the last name.

When you access the data, It’s more efficient to specify the columns in the right order as in the index definition. So, here, it should be first name, then last name, and not the vice-versa.

## Clustered & Non-Clustered Indexes

A table can have only one clustered index, while it can have more than one non-clustered index.

**Clustered index**

Every table can have one and only one clustered index. The most common clustered index in any database table is the primary key column.

The database will then order the data in the table based on the clustered index; no Index table need to be created. The binary search algorithm will be used to get to the required data in the table (already ordered).

**Non-Clustered index**

If you found yourself often also accessing the data using another column, we can create a secondary index; a non-clustered index.

Let’s say we want to create a secondary index for the last name, while the clustered index is the employee id. It’s created in a separate table, it has two columns, one for the last name, and one for the corresponding employee id.

The created table is now sorted by last name, the way that we can’t actually do in the employee table, because we’re already sorted by the employee id.

Now it’s not as quick as using the clustered index. Why? We still need to read from the table created for secondary index then jump to the employee table to get to a specific employee. But, it’s much quicker than a full table scan.

![clustered](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/clustered.png)

## Advantages/Disadvantages of using indexes

**Advantages**

* Speed up SELECT query
* Helps to make a row unique or without duplicates(primary,unique) 
* If index is set to fill-text index, then we can search against large string values. for example to find a word from a sentence etc.

**Disadvantages**

* Indexes take additional disk space.
* Indexes slow down INSERT,UPDATE and DELETE, but will speed up UPDATE if the WHERE condition has an indexed field.  INSERT, UPDATE and DELETE becomes slower because on each operation the indexes must also be updated. 

## Implementation

As we mentioned previously in the SQL tutorial, DDL operations manage table and index structure. That is, we can CREATE, ALTER, or DROP an index.

The syntax to create and delete indexes varies among different databases. Therefore, you need to check the syntax for creating indexes in your database. We’ll use MySQL to get an idea on how they can be created, and deleted.

**CREATE**

There are two ways to create an index, either when creating a table, or using the CREATE INDEX statement.

```
-- Create an index in CREATE TABLE (duplicate values are allowed)
CREATE TABLE books (
    title VARCHAR(255),
    INDEX index_name (title)
);

-- Create an index in CREATE TABLE (duplicate values aren't allowed)
CREATE TABLE books (
    title VARCHAR(255),
    UNIQUE INDEX index_name (title)
);

-- Create an index (duplicate values are allowed)
CREATE INDEX index_name ON table_name (column_name);

-- Create a unique index (duplicate values aren't allowed)
CREATE UNIQUE INDEX index_name ON table_name (column_name);
```

The CREATE INDEX statement is mapped to an ALTER TABLE statement to create indexes.

If you want to create an index on a combination of columns, you can list the column names within the parentheses, separated by commas.

```
CREATE INDEX index_name ON table_name (column_A, column_B, ...);
```

The index table will be sorted on column A, then with A, there would be the B’s in order as well. So, It’s more efficient to specify the columns in the order as in the index definition to speed up queries on the table.

**ALTER**

The ALTER TABLE statement changes the structure of a table. One example is to create or destroy indexes.

```
-- Add an index to existing table
ALTER TABLE tbl_name ADD INDEX index_name (col_name);

-- Add a unique (no duplicates) index to existing table
ALTER TABLE tbl_name ADD UNIQUE INDEX index_name (col_name);

-- Delete an index in an existing table
ALTER TABLE tbl_name DROP INDEX index_name;
```

**DROP**

The DROP INDEX statement deletes an index a table. The DROP INDEX statement is mapped to an ALTER TABLE statement to drop the index. 

```
DROP INDEX index_name ON tbl_name;
```

# SQL Constraints

SQL constraints are used to specify rules for the data in a table.

Constraints are used to limit the type of data that can go into a table. This ensures the accuracy and reliability of the data in the table. If there is any violation between the constraint and the data action, the action is aborted.

Constraints can be column level or table level. Column level constraints apply to a column, and table level constraints apply to the whole table.

The following constraints are commonly used in SQL:

* NOT NULL - Ensures that a column cannot have a NULL value
* UNIQUE - Ensures that all values in a column are different
* PRIMARY KEY - A combination of a NOT NULL and UNIQUE. Uniquely identifies each row in a table
* FOREIGN KEY - Uniquely identifies a row/record in another table
* CHECK - Ensures that all values in a column satisfies a specific condition
* DEFAULT - Sets a default value for a column when no value is specified

SQL snippets below adopted for MySQL

### NOT NULL Constraint

By default, a column can hold NULL values.

The NOT NULL constraint enforces a column to NOT accept NULL values.

This enforces a field to always contain a value, which means that you cannot insert a new record, or update a record without adding a value to this field.

The following SQL ensures that the "ID", "LastName", and "FirstName" columns will NOT accept NULL values:

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```

### UNIQUE Constraint

The UNIQUE constraint ensures that all values in a column are different.

Both the UNIQUE and PRIMARY KEY constraints provide a guarantee for uniqueness for a column or set of columns.

A PRIMARY KEY constraint automatically has a UNIQUE constraint.

However, you can have many UNIQUE constraints per table, but only one PRIMARY KEY constraint per table.

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    UNIQUE (ID)
);
```

To name a UNIQUE constraint, and to define a UNIQUE constraint on multiple columns, use the following SQL syntax:

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT UC_Person UNIQUE (ID,LastName)
);
```

### PRIMARY KEY Constraint

The PRIMARY KEY constraint uniquely identifies each record in a database table.

Primary keys must contain UNIQUE values, and cannot contain NULL values.

A table can have only one primary key, which may consist of single or multiple fields.

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    PRIMARY KEY (ID)
);
```

To allow naming of a PRIMARY KEY constraint, and for defining a PRIMARY KEY constraint on multiple columns, use the following SQL syntax:

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CONSTRAINT PK_Person PRIMARY KEY (ID,LastName)
);
```

### FOREIGN KEY Constraint

A FOREIGN KEY is a key used to link two tables together.

A FOREIGN KEY is a field (or collection of fields) in one table that refers to the PRIMARY KEY in another table.

The table containing the foreign key is called the child table, and the table containing the candidate key is called the referenced or parent table.

Look at the following two tables:

"Persons" table:

![clustered](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/persons.png)

"Orders" table:

![clustered](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/orders.png)

Notice that the "PersonID" column in the "Orders" table points to the "PersonID" column in the "Persons" table.

The "PersonID" column in the "Persons" table is the PRIMARY KEY in the "Persons" table.

The "PersonID" column in the "Orders" table is a FOREIGN KEY in the "Orders" table.

The FOREIGN KEY constraint is used to prevent actions that would destroy links between tables.

The FOREIGN KEY constraint also prevents invalid data from being inserted into the foreign key column, because it has to be one of the values contained in the table it points to.

### CHECK Constraint

The CHECK constraint is used to limit the value range that can be placed in a column.

If you define a CHECK constraint on a single column it allows only certain values for this column.

If you define a CHECK constraint on a table it can limit the values in certain columns based on values in other columns in the row.

```
CHECK constraint on the "Age" column when the "Persons" table is created. The CHECK constraint ensures that you can not have any person below 18 years:

CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    CHECK (Age>=18)
);

To create a CHECK constraint on the "Age" column when the table is already created, use the following SQL:

ALTER TABLE Persons
ADD CHECK (Age>=18);

ALTER TABLE Persons
ADD CONSTRAINT CHK_PersonAge CHECK (Age>=18 AND City='Sandnes');

Drop check

ALTER TABLE Persons
DROP CHECK CHK_PersonAge;
```

### DEFAULT Constraint

The DEFAULT constraint is used to provide a default value for a column.
  
The default value will be added to all new records IF no other value is specified.

```
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int,
    City varchar(255) DEFAULT 'Sandnes'
);

ALTER TABLE Persons
ALTER City SET DEFAULT 'Sandnes';

ALTER TABLE Persons
ALTER City DROP DEFAULT;
```

# Triggers

A database trigger is procedural code that is automatically executed in response to certain events on a particular table or view in a database. The trigger is mostly used for maintaining the integrity of the information on the database. For example, when a new record (representing a new worker) is added to the employees table, new records should also be created in the tables of the taxes, vacations and salaries. Triggers can also be used to log historical data, for example to keep track of employees' previous salaries.

Triggers are event-condition-action rules.

They specify that whenever a certain type of event occurs in the database, check the condition over the database and if it's true execute an action automatically.

Triggers can be written for the following purposes:

* Generating some derived column values automatically
* Enforcing referential integrity
* Event logging and storing information on table access
* Auditing
* Synchronous replication of tables
* Imposing security authorizations
* Preventing invalid transactions

**Implementations for different RDBMS vary significantly**

## Trigger structure

```
CREATE [OR REPLACE ] TRIGGER trigger_name  
{BEFORE | AFTER | INSTEAD OF }  
{INSERT [OR] | UPDATE [OR] | DELETE}  
[OF col_name]  
ON table_name  
[REFERENCING OLD AS o NEW AS n]  
[FOR EACH ROW]  
WHEN (condition)   
action
```

* CREATE [OR REPLACE] TRIGGER trigger_name − Creates or replaces an existing trigger with the trigger_name.
* {BEFORE | AFTER | INSTEAD OF} − This specifies when the trigger will be executed. The INSTEAD OF clause is used for creating trigger on a view.
* {INSERT [OR] | UPDATE [OR] | DELETE} − This specifies the DML operation.
* [OF col_name] − This specifies the column name that will be updated.
* [ON table_name] − This specifies the name of the table associated with the trigger.
* [REFERENCING OLD AS o NEW AS n] − This allows you to refer new and old values for various DML statements, such as INSERT, UPDATE, and DELETE.
* [FOR EACH ROW] − This specifies a row-level trigger, i.e., the trigger will be executed for each row being affected. Otherwise the trigger will execute just once when the SQL statement is executed, which is called a table level trigger.
* WHEN (condition) − This provides a condition for rows for which the trigger would fire. This clause is valid only for row-level triggers.

## Triggers examples

Designed for SQLite. Relations are the same as in SQL Examples section.

AFTER-INSERT TRIGGER - New students with GPA between 3.3 and 3.6 automatically apply to geology major at Stanford and biology at MIT

```
create trigger R1
after insert on Student
for each row
when New.GPA > 3.3 and New.GPA <= 3.6
begin
  insert into Apply values (New.sID, 'Stanford', 'geology', null);
  insert into Apply values (New.sID, 'MIT', 'biology', null);
end;
```

AFTER-DELETE TRIGGER - Cascaded delete for Apply(sID) references Student(sID)

```
create trigger R2
after delete on Student
for each row
begin
  delete from Apply where sID = Old.sID;
end;
```

AFTER-UPDATE TRIGGER - Cascaded update for Apply(cName) references College(cName)

```
create trigger R3
after update of cName on College
for each row
begin
  update Apply
  set cName = New.cName
  where cName = Old.cName;
end;
```

BEFORE TRIGGERS, ACTION RAISING ERROR - Enforce key constraint on College.cName (ignore colleges with same names)

```
create trigger R4
before insert on College
for each row
when exists (select * from College where cName = New.cName)
begin
  select raise(ignore);
end;

create trigger R5
before update of cName on College
for each row
when exists (select * from College where cName = New.cName)
begin
  select raise(ignore);
end;
```

TRIGGER CHAINING - When number of applicants exceeds 10, label College as 'Done'

```
create trigger R6
after insert on Apply
for each row
when (select count(*) from Apply where cName = New.cName) > 10
begin
  update College set cName = cName || '-Done'
  where cName = New.cName;
end;
```

MORE COMPLEX TRIGGER - Automatically accept to Berkeley students with high GPAs from large high schools

```
create trigger AutoAccept
after insert on Apply
for each row
when (New.cName = 'Berkeley' and
      3.7 < (select GPA from Student where sID = New.sID) and
      1200 < (select sizeHS from Student where sID = New.sID))
begin
  update Apply
  set decision = 'Y'
  where sID = New.sID
  and cName = New.cName;
end;
```

# Views

In a database, a view is the result set of a stored query on the data, which the database users can query just as they would in a persistent database collection object. This pre-established query command is kept in the database dictionary. Unlike ordinary base tables in a relational database, a view does not form part of the physical schema: as a result set, it is a virtual table computed or collated dynamically from data in the database when access to that view is requested. Changes applied to the data in a relevant underlying table are reflected in the data shown in subsequent invocations of the view.

A view is nothing more than a SQL statement that is stored in the database with an associated name. A view is actually a composition of a table in the form of a predefined SQL query.

A view can contain all rows of a table or select rows from a table. A view can be created from one or many tables which depends on the written SQL query to create a view.

Views can provide advantages over tables:

* Views can represent a subset of the data contained in a table. Consequently, a view can limit the degree of exposure of the underlying tables to the outer world: a given user may have permission to query the view, while denied access to the rest of the base table.
* Views can join and simplify multiple tables into a single virtual table.
* Views can act as aggregated tables, where the database engine aggregates data (sum, average, etc.) and presents the calculated results as part of the data.
* Views can hide the complexity of data. For example, a view could appear as Sales2000 or Sales2001, transparently partitioning the actual underlying table.
* Views take very little space to store; the database contains only the definition of a view, not a copy of all the data that it presents.
* Depending on the SQL engine used, views can provide extra security.

Just as a function (in programming) can provide abstraction, so can a database view. In another parallel with functions, database users can manipulate nested views, thus one view can aggregate data from other views. Without the use of views, the normalization of databases above second normal form would become much more difficult. Views can make it easier to create lossless join decomposition.

## Read-only/updatable views

Database practitioners can define views as read-only or updatable. If the database system can determine the reverse mapping from the view schema to the schema of the underlying base tables, then the view is updatable. INSERT, UPDATE, and DELETE operations can be performed on updatable views. Read-only views do not support such operations because the DBMS cannot map the changes to the underlying base tables. A view update is done by key preservation.

Some systems support the definition of INSTEAD OF triggers on views. This technique allows the definition of other logic for execution in place of an insert, update, or delete operation on the views. Thus database systems can implement data modifications based on read-only views. However, an INSTEAD OF trigger does not change the read-only or updatable property of the view itself.

## SQL for dealing with views

SIMPLE ONE-TABLE VIEW - Student ID and college name of CS acceptances

```
create view CSaccept as
select sID, cName
from Apply
where major = 'CS' and decision = 'Y';
```

VIEW LAYERING - Students accepted to CS at Berkeley with sizeHS > 500

```
create view CSberk as
select Student.sID, sName, GPA
from Student, CSaccept
where Student.sID = CSaccept.sID and cName = 'Berkeley' and sizeHS > 500;

```

DROP VIEW

```
drop view CSaccept;
```

## Materialized view

In computing, a materialized view is a database object that contains the results of a query. For example, it may be a local copy of data located remotely, or may be a subset of the rows and/or columns of a table or join result, or may be a summary using an aggregate function.

In any database management system following the relational model, a view is a virtual table representing the result of a database query. Whenever a query or an update addresses an ordinary view's virtual table, the DBMS converts these into queries or updates against the underlying base tables. A materialized view takes a different approach: the query result is cached as a concrete ("materialized") table (rather than a view as such) that may be updated from the original base tables from time to time. This enables much more efficient access, at the cost of extra storage and of some data being potentially out-of-date. Materialized views find use especially in data warehousing scenarios, where frequent queries of the actual base tables can be expensive.

The integrity of data in materialized views is supported by periodic synchronization or using triggers.

# Stored procedures

A stored procedure is a database object that is a set of SQL statements that is compiled once and stored on the server. Stored procedures are very similar to ordinary procedures of high-level languages, they can have input and output parameters and local variables, they can perform numerical calculations and operations on symbolic data, the results of which can be assigned to variables and parameters. Stored procedures can perform standard database operations (both DDL and DML). In addition, in stored procedures, loops and branchings are possible, that is, instructions for controlling the execution process can be used.

Uses for stored procedures include data-validation (integrated into the database) or access-control mechanisms. Furthermore, stored procedures can consolidate and centralize logic that was originally implemented in applications. To save time and memory, extensive or complex processing that requires execution of several SQL statements can be saved into stored procedures, and all applications call the procedures. One can use nested stored procedures by executing one stored procedure from within another.

Stored procedures may return result sets, i.e., the results of a SELECT statement. Such result sets can be processed using cursors, by other stored procedures, by associating a result-set locator, or by applications. Stored procedures may also contain declared variables for processing data and cursors that allow it to loop through multiple rows in a table. Stored-procedure flow-control statements typically include IF, WHILE, LOOP, REPEAT, and CASE statements, and more. Stored procedures can receive variables, return results or modify variables and return them, depending on how and where the variable is declared.

## SP Advantages

**Overhead**

Because stored procedure statements are stored directly in the database, they may remove all or part of the compiling overhead that is typically needed in situations where software applications send inline (dynamic) SQL queries to a database. (However, most database systems implement statement caches and other methods to avoid repetitively compiling dynamic SQL statements.) Also, while they avoid some pre-compiled SQL, statements add to the complexity of creating an optimal execution plan because not all arguments of the SQL statement are supplied at compile time. Depending on the specific database implementation and configuration, mixed performance results will be seen from stored procedures versus generic queries or user defined functions.

**Avoiding network traffic**

A major advantage of stored procedures is that they can run directly within the database engine. In a production system, this typically means that the procedures run entirely on a specialized database server, which has direct access to the data being accessed. The benefit here is that network communication costs can be avoided completely. This becomes more important for complex series of SQL statements.

**Encapsulating business logic**

Stored procedures allow programmers to embed business logic as an API in the database, which can simplify data management and reduce the need to encode the logic elsewhere in client programs. This can result in a lesser likelihood of data corruption by faulty client programs. The database system can ensure data integrity and consistency with the help of stored procedures.

**Delegating access-rights**

In many systems, stored procedures can be granted access rights to the database that users who execute those procedures do not directly have.

**Some protection from SQL injection attacks**

Stored procedures can be used to protect against injection attacks. Stored procedure parameters will be treated as data even if an attacker inserts SQL commands. Also, some DBMS will check the parameter's type. However, a stored procedure that in turn generates dynamic SQL using the input is still vulnerable to SQL injections unless proper precautions are taken.

## SP Disadvantages

* **Stored procedure languages are often vendor-specific.** Changing database vendors usually requires rewriting existing stored procedures.
* Stored procedure languages from different vendors have different levels of sophistication. For example, Postgres' pgpsql has more language features (especially via extensions) than Microsoft's T-SQL.
* Tool support for writing and debugging stored procedures is often not as good as for other programming languages, but this differs between vendors and languages. For example, both PL/SQL and T-SQL have dedicated IDEs and debuggers. PL/PgSQL can be debugged from various IDEs.
* Changes to stored procedures are harder to keep track of within a version control system than other code. Changes must be reproduced as scripts to be stored in the project history to be included, and differences in procedures can be harder to merge and track correctly.

# Scalability

Historically, database systems adopted two main approaches to scalability, which enables a database to accommodate more user data and process more application workload. They would scale up (called vertical scalability) and scale out (called horizontal scalability).

Scalability can be measured in various dimensions, such as:

* Administrative scalability: The ability for an increasing number of organizations or users to easily share a single distributed system.
* Functional scalability: The ability to enhance the system by adding new functionality at minimal effort.
* Geographic scalability: The ability to maintain performance, usefulness, or usability regardless of expansion from concentration in a local area to a more distributed geographic pattern.
* Load scalability: The ability for a distributed system to easily expand and contract its resource pool to accommodate heavier or lighter loads or number of inputs. Alternatively, the ease with which a system or component can be modified, added, or removed, to accommodate changing load.
* Generation scalability: The ability of a system to scale up by using new generations of components. Thereby, heterogeneous scalability is the ability to use the components from different vendors

## Vertical Database Scalability

To scale up usually refers to adding more physical resources — that is, increasing CPU, memory, and storage for an existing server or adding a bigger one. In essence with vertical scalability:

* Application compatibility is prioritized—there’s no need for code changes.
* Administrative efforts are reduced with only a single system image to manage.
* Hardware configurations tend to be more expensive, although today’s quickly evolving hardware provides incredibly efficient server components with great price-performance ratios.
* Software costs (typically charged by the number of cores) can increase.

This approach also comes with at least a couple of limitations:

* What happens when a workload cannot fit onto the best-equipped hardware configuration?
* What if a workload is highly variable? Why make an upfront investment in an expensive, large-capacity system that could go underutilized much of the time? For this reason alone, many cloud providers do not rely solely on vertical scalability.

## Horizontal Database Scalability

Horizontal scalability accommodates variable workloads by hosting data across multiple databases. Unlike vertical scalability, scale-out approaches can help reduce costs by making use of less sophisticated hardware components, freeing resources for more in-application development and data and system maintenance.

You can use any of several well-known approaches to scaling out data tiers. The one you choose depends on your workload and the applications supported by the data store. Most people choose functional partitioning in which a data set is decomposed into business or organizational functionalities.

Three main concepts for horizontal database scalability are:

* Partition
* Replication
* Sharding

## Partition

A partition is a division of a logical database or its constituent elements (tables) into distinct independent parts. Database partitioning is normally done for manageability, performance or availability reasons, or for load balancing.

A popular application of partitioning is in a distributed database management system. Each partition may be spread over multiple nodes, and users at the node can perform local transactions on the partition. 

**Partitioning criteria**

Current high end relational database management systems provide for different criteria to split the database. They take a partitioning key and assign a partition based on certain criteria. Common criteria are:

* **Range partitioning** - selects a partition by determining if the partitioning key is inside a certain range. An example could be a partition for all rows where the column zipcode has a value between 70000 and 79999. It distributes tuples based on the value intervals (ranges) of some attribute. In addition to supporting exact-match queries (as in hashing), it is well-suited for range queries. For instance, a query with a predicate “A between A1 and A2” may be processed by the only node(s) containing tuples.
* **List partitioning** - a partition is assigned a list of values. If the partitioning key has one of these values, the partition is chosen. For example, all rows where the column Country is either Iceland, Norway, Sweden, Finland or Denmark could build a partition for the Nordic countries.
* **Composite partitioning** - allows for certain combinations of the above partitioning schemes, by for example first applying a range partitioning and then a hash partitioning. Consistent hashing could be considered a composite of hash and list partitioning where the hash reduces the key space to a size that can be listed.
* **Round-robin partitioning** - the simplest strategy, it ensures uniform data distribution. With n partitions, the ith tuple in insertion order is assigned to partition (i mod n). This strategy enables the sequential access to a relation to be done in parallel. However, the direct access to individual tuples, based on a predicate, requires accessing the entire relation.
* **Hash partitioning** - applies a hash function to some attribute that yields the partition number. This strategy allows exact-match queries on the selection attribute to be processed by exactly one node and all other queries to be processed by all the nodes in parallel.

**Partitioning methods**

The partitioning can be done by either building separate smaller databases (each with its own tables, indices, and transaction logs), or by splitting selected elements, for example just one table.

Horizontal partitioning involves putting different rows into different tables. For example, customers with ZIP codes less than 50000 are stored in CustomersEast, while customers with ZIP codes greater than or equal to 50000 are stored in CustomersWest. The two partition tables are then CustomersEast and CustomersWest, while a view with a union might be created over both of them to provide a complete view of all customers.

Vertical partitioning involves creating tables with fewer columns and using additional tables to store the remaining columns. Normalization also involves this splitting of columns across tables, but vertical partitioning goes beyond that and partitions columns even when already normalized. Different physical storage might be used to realize vertical partitioning as well; storing infrequently used or very wide columns on a different device, for example, is a method of vertical partitioning. Done explicitly or implicitly, this type of partitioning is called "row splitting" (the row is split by its columns). A common form of vertical partitioning is to split dynamic data (slow to find) from static data (fast to find) in a table where the dynamic data is not used as often as the static. Creating a view across the two newly created tables restores the original table with a performance penalty, however performance will increase when accessing the static data e.g. for statistical analysis.

## Replication

The mechanism for synchronizing the contents of multiple copies of an object (for example, the contents of a database).

### Master-slaves replication

The master logs the updates, which then ripple through to the slaves. The slave outputs a message stating that it has received the update successfully, thus allowing the sending (and potentially re-sending until successfully applied) of subsequent updates.

The main database server is available for reading and writing, the replica is readable or not available at all. The data on the matser and the replica are identical.

![clustered](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/db_replication.jpg)

### Multi masters replication

Multi-master replication is a method of database replication which allows data to be stored by a group of computers, and updated by any member of the group. All members are responsive to client data queries. The multi-master replication system is responsible for propagating the data modifications made by each member to the rest of the group, and resolving any conflicts that might arise between concurrent changes made by different members.

Multi-master replication can be contrasted with master-slave replication, in which a single member of the group is designated as the "master" for a given piece of data and is the only node allowed to modify that data item. Other members wishing to modify the data item must first contact the master node. Allowing only a single master makes it easier to achieve consistency among the members of the group, but is less flexible than multi-master replication.

Multi-master replication can also be contrasted with failover clustering where passive slave servers are replicating the master data in order to prepare for takeover in the event that the master stops functioning. The master is the only server active for client interaction.

The primary purposes of multi-master replication are increased availability and faster server response time.

**Advantages**

* If one master fails, other masters continue to update the database.
* Masters can be located in several physical sites, i.e. distributed across the network.

**Disadvantages**

* Most multi-master replication systems are only loosely consistent, i.e. lazy and asynchronous, violating ACID properties.
* Eager replication systems are complex and increase communication latency.
* Issues such as conflict resolution can become intractable as the number of nodes involved rises and latency increases.

![clustered](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/repl-multinode-04.gif)

## Sharding

A database shard is a horizontal partition of data in a database or search engine. Each individual partition is referred to as a shard or database shard. Each shard is held on a separate database server instance, to spread load.

Some data within a database remains present in all shards, but some appears only in a single shard. Each shard (or server) acts as the single source for this subset of data.

### Sharding Database architecture

Horizontal partitioning is a database design principle whereby rows of a database table are held separately, rather than being split into columns (which is what normalization and vertical partitioning do, to differing extents). Each partition forms part of a shard, which may in turn be located on a separate database server or physical location.

There are numerous advantages to the horizontal partitioning approach. Since the tables are divided and distributed into multiple servers, the total number of rows in each table in each database is reduced. This reduces index size, which generally improves search performance. A database shard can be placed on separate hardware, and multiple shards can be placed on multiple machines. This enables a distribution of the database over a large number of machines, greatly improving performance. In addition, if the database shard is based on some real-world segmentation of the data (e.g., European customers v. American customers) then it may be possible to infer the appropriate shard membership easily and automatically, and query only the relevant shard.

Sharding a database table before it has been optimized locally causes premature complexity. Sharding should be used only when all other options for optimization are inadequate. The introduced complexity of database sharding causes the following potential problems:

* Increased complexity of SQL - Increased bugs because the developers have to write more complicated SQL to handle sharding logic.
* Sharding introduces complexity - The sharding software that partitions, balances, coordinates, and ensures integrity can fail.
* Single point of failure - Corruption of one shard due to network/hardware/systems problems causes failure of the entire table.
* Failover servers more complex - Failover servers must themselves have copies of the fleets of database shards.
* Backups more complex - Database backups of the individual shards must be coordinated with the backups of the other shards.
* Operational complexity added - Adding/removing indexes, adding/deleting columns, modifying the schema becomes much more difficult.

These historical complications of do-it-yourself sharding were addressed by independent software vendors who provided automatic sharding.

In practice, sharding is complex. Although it has been done for a long time by hand-coding (especially where rows have an obvious grouping, as per the example above), this is often inflexible. There is a desire to support sharding automatically, both in terms of adding code support for it, and for identifying candidates to be sharded separately. Consistent hashing is a technique used in sharding to spread large loads across multiple smaller services and servers.[3]

Where distributed computing is used to separate load between multiple servers (either for performance or reliability reasons), a shard approach may also be useful.

![clustered](https://scm.vinsys.live/nilesh.devdas/dbgrads/raw/master/db/readme/img/sharding.jpg)

### Shards compared to horizontal partitioning

Horizontal partitioning splits one or more tables by row, usually within a single instance of a schema and a database server. It may offer an advantage by reducing index size (and thus search effort) provided that there is some obvious, robust, implicit way to identify in which partition a particular row will be found, without first needing to search the index, e.g., the classic example of the 'CustomersEast' and 'CustomersWest' tables, where their zip code already indicates where they will be found.

Sharding goes beyond this: it partitions the problematic table(s) in the same way, but it does this across potentially multiple instances of the schema. The obvious advantage would be that search load for the large partitioned table can now be split across multiple servers (logical or physical), not just multiple indexes on the same logical server.

Splitting shards across multiple isolated instances requires more than simple horizontal partitioning. The hoped-for gains in efficiency would be lost, if querying the database required both instances to be queried, just to retrieve a simple dimension table. Beyond partitioning, sharding thus splits large partitionable tables across the servers, while smaller tables are replicated as complete units.

This is also why sharding is related to a shared nothing architecture—once sharded, each shard can live in a totally separate logical schema instance / physical database server / data center / continent. There is no ongoing need to retain shared access (from between shards) to the other unpartitioned tables in other shards.

This makes replication across multiple servers easy (simple horizontal partitioning does not). It is also useful for worldwide distribution of applications, where communications links between data centers would otherwise be a bottleneck.

There is also a requirement for some notification and replication mechanism between schema instances, so that the unpartitioned tables remain as closely synchronized as the application demands. This is a complex choice in the architecture of sharded systems: approaches range from making these effectively read-only (updates are rare and batched), to dynamically replicated tables (at the cost of reducing some of the distribution benefits of sharding) and many options in between.



# Intro to NoSQL with Mongo

**This lesson is adapted from Jim Clark / Micah Rich's original lesson in the WDI repo**

### Objectives
- Describe how Mongo databases came about & why they're useful
- Compare and contrast NoSQL with SQL
- Define what a document is in the context of MongoDB
- Explain the difference between embedded and referenced documents, and how we use each to model relationships in MongoDB
- Issue basic CRUD commands to a database from the Mongo Shell

### Preparation
- Create an Express app from scratch
- Either a local MongoDB installation or [Vagrant box for MongoDB](https://github.com/bobthecow/vagrant-mongobox)

## What is MongoDB - Intro 

#### Overview - Mongo & NoSQL Databases

MongoDB is one of the new breeds of databases known as NoSQL databases. NoSQL databases are heavily used in real time, big data and social media applications and generally called NoSQL because they do things a little differently than traditional SQL databases. We'll see what that means in a minute.

So you know – there are software "drivers" that allow MongoDB to be used with a multitude of programming languages and frameworks, including both Node and Ruby on Rails. We'll be talking about it in Express applications later today. If you want to research using it in Sinatra or Rails, take a look at the `mongoid` gem.

For this module, we're using straight up Mongo. So what's a Mongo database look like?

#### Data Format

- A MongoDB database consists of _documents_.
- A _document_ in MongoDB is composed of _field_ and _value_ pairs.
- Hint: remember our relational database (SQL) tables? You can think of each of these _documents_ as a row in your table.
Let's take a look of what a MongoDB _document_ may look like:

```js
{
    _id: ObjectId("5099803df3f4948bd2f98391"),
    name: { first: "Alan", last: "Turing" },
    birth: new Date('Jun 23, 1912'),
    death: new Date('Jun 07, 1954'),
    contribs: [ "Turing machine", "Turing test", "Turingery" ],
    views: 1250000
}
```

__What does this data structure remind you of?__ JSON!

A MongoDB _document_ is very much like JSON, except it is stored in the database in a format known as _BSON_ (think - _Binary JSON_).

_BSON_ basically extends _JSON_ with additional data types, such as __ObjectID__ and __Date__ shown above.

#### The Document *_id*

The *_id* is a special field represents the document's _primary key_ and will always be listed as the first field. It must be unique.

We can explicitly set the *_id* like this:

```js
{
  _id: 2,
  name: "Suzy"
}
```
or this...

```js
{
  _id: "ABC",
  name: "Suzy"
}
```
However, it's more common to allow MongoDB to create it implicitly for us using its _ObjectID_ data type.


#### MongoDB vs. Relational SQL Databases, Terminology

![](http://4.bp.blogspot.com/-edz2_QrFvCE/UnzBhKZE3FI/AAAAAAAAAEs/bTEsqnZFTXw/s1600/SQL-MongoDB+Correspondence.PNG)

#### Key Differences of MongoDB

- Schema-less
The documents in a MongoDB collection can have completely different types and number of fields from each other.<br>__How does this compare to a SQL database like PostgreSQL?__

- No Table Joins
In a SQL DB, we break up related data into separate tables.

In MongoDB, we often _embed_ related data in a single document, you'll see an example of this later.

The supporters of MongoDB highlight the lack of table joins as a performance advantage since joins are expensive in terms of computer processing.

## Installing, Creating a DB, and Inserting Documents - Codealong 

#### Installation

You may already have MongoDB installed on your system, lets check in terminal `which mongod` (note the lack of a "b" at the end").

If you get `/usr/local/bin/mongod`, you're golden!

If you get a null response, lets use _Homebrew_ to install MongoDB:

1. Update Homebrew's database (this might take a bit of time)<br>`brew update`
2. Then install MongoDB

 `brew install mongodb`

1. MongoDB by default will look for data in a folder named `/data/db`. We would have had to create this folder, but Homebrew did it for us (hopefully).
   1. run this command in your terminal:
```shell
[ ! -d /data/db ] && sudo mkdir -p /data/db && sudo chown -R $(whoami) /data/db || ls -la /data
```
   2. You should get something like this:
```shell
total 0
drwxr-xr-x   3 root       wheel   102 Nov 11 13:06 .
drwxr-xr-x  38 root       wheel  1360 Nov 11 13:06 ..
drwxr-xr-x   8 jseminara  wheel   272 Nov 11 13:10 db
```



#### Start Your Engine

`mongod` is the name of the actual database engine process. The installation of MongoDB does not set mongoDB to start automatically. A common source of errors when starting to work with MongoDB is forgetting to start the database engine.

To start the database engine, type `mongod` in terminal.

Press `control-c` to stop the engine.

#### Creating a Database and Inserting Documents

MongoDB installs with a client app, a JavaScript-based shell, that allows us to interact with MongoDB directly.

Start the app in terminal by typing `mongo`.

The app will load and change the prompt will change to `>`.

List the shell's commands available: `> help`.

Show the list of databases: `> show dbs`.

Show the name of the currently active database: `> db`.

Switch to a different database: `> use [name of database to switch to]`.

Let's switch to the `local` database: `> use local`.

Show the collections of the current database `> show collections`.

#### Creating a new Database

To create a new database in the Mongo Shell, we simply have to _use_ the database.  Let's create a database named _myDB_:

```
> use myDB
```

#### Inserting Data into a Collection

This how we can create and insert a document into a collection named _people_:

```
> db.people.insert({
    name: "Fred", // Don't type the dots, they are from the
    age: 21     // shell, indicating multi-line mode
})
```

Using a collection for the first time creates it!

#### Adding Lots of New Documents

In a moment we'll practice querying our database, but let's get more data in there. Here are few more documents to put in your _people_ collection. We can simply provide this __array__ to the _insert_ method and it will create a document for each object in the array.

```js
db.people.insert([
  {
    "name": "Emma",
    "age": 20
  },
  {
    "name": "Ray",
    "age": 45
  },
  {
    "name": "Celeste",
    "age": 33
  },
  {
    "name": "Stacy",
    "age": 53
  },
  {
    "name": "Katie",
    "age": 12
  },
  {
    "name": "Adrian",
    "age": 47
  }
]);
```

> Note: Be sure to type the closing parent of the _insert_ method!


## Querying Documents - Codealong (10 mins)

To list all documents in a collection, we use the _find_ method on the collection without any arguments:

```
> db.people.find()
```

Again, unlike the rows in a relational database, our documents don't have to have the same fields!

### More Specific Queries

We can also use the `find()` method to query the collection by passing in an argument – a JS object containing criteria to query with.

```
> db.people.find( {name: "Emma"} )

```

There are a handful of special criteria variables we can use, too. Here's how we can use MongoDB's `$gt` query operator to return all _people_ documents with an age greater than 20:

```
> db.people.find( {age: { $gt: 20 } } )
```

MongoDB comes with a slew of built-in [query operators](http://docs.mongodb.org/manual/reference/operator/query/#query-selectors) we can use to write complex queries.

__How would we write a query to retrieve people that are less than or equal to age 20?__

In addition to selecting which data is returned, we can modify how that data is returned by limiting the number of documents returned, sorting the documents, and by projecting which fields are returned.

This sorts our age query and sorts by _name_:

```
> db.people.find( {age: { $gt: 20 } } ).sort( {name: 1} )
```
The "1" indicates ascending order.

[This documentation](http://docs.mongodb.org/manual/core/read-operations-introduction/) provides more detail about reading data.

## Updating Data - Codealong

In MongoDB, we use the `update()` method of collections by specifying the _update criteria_ (like we did with `find()`), and use the `$set` action to set the new value.

```
> db.people.update( { name: "Emma" }, { $set: { age: 99 } })
```

By default `update()` will only modify a single document. However, with the `multi` option, we can update all of the documents that match the query.

```
> db.people.update( { name: { $lt: "M" } }, { $inc: { age: 10 } }, { multi: true } )
```
We used the `$inc` update operator to increase the existing value.

Here is the [list of Update Operators](http://docs.mongodb.org/manual/reference/operator/update/) available.

## Removing Data - Codealong 

We use the `remove()` method to data from collections.

If you want to completely remove a collection, including all of its indexes, use `[name of the collection].drop()`.

Call `remove({})` on the collection to remove all docs from a collection. Note: all documents will match the "empty" criteria.

Otherwise, specify a criteria to remove all documents that match it:

```
> db.people.remove( { age: { $lt: 50 } } )
```

## Data Modeling in MongoDB - Intro

There are two ways to modeling related data in MongoDB:

- via __embedding__
- via __referencing__ (linking)

Both approaches can be used simultaneously in the same document.

### Embedded Documents

In MongoDB, by design, it is common to __embed__ data in a parent document.

Modeling data with the __embedded__ approach is different than what we've seen in a relational DB where we spread our data across multiple tables. However, this is the way MongoDB is designed to work and is the reason MongoDB can read and return large amounts of data far more quickly than a SQL DB that requires join operations.

To demonstrate __embedding__, we will add another person to our _people_ collection, but this time we want to include contact info. A person may have several ways to contact them, so we will be modeling a typical one-to-many relationship.

## Modeling Data - Codealong

Let's walk through this command by entering it together:

```js
> db.people.insert({
    name: "Manny",
    age: 33,
    contacts: [
      {
        type: "email",
        contact: "manny@domain.com"
      },
      {
        type: "mobile",
        contact: "(555) 555-5555"
      }
    ]})
```

__What do you imagine could be a downside of embedding data?__

If the embedded data's growth is unbound, MongoDB's maximum document size of 16 megabytes could be exceeded.

The above approach of embedding _contact_ documents provides a great deal of flexibility in what types and how many contacts a person may have.  However, this flexibility slightly complicates querying.

However, what if our app only wanted to work with a person's multiple _emails_ and _phoneNumbers_?

__Knowing this, pair up and discuss how you might alter the above structure.__

#### Referencing Documents

We can model data relationships using a __references__ approach where data is stored in separate documents. These documents, due to the fact that they hold different types of data, are likely be stored in separate collections.

It may help to think of this approach as _linking_ documents together by including a reference to the related document's *_id* field.

Let's create a new `bankAccounts` collection:

```js
> use bankAccounts
```

> Note: Use the idea that the person might have a _joint account_, which is owned by more than one person.

For the sake of _data consistency_, keeping the account data in its own document would be a better design decision. In more clear terms, it would not be a good idea to store a bank account's balance in more than one place.

In our app, we have decided that all bank accounts will be retrieved through a person. This decision allows us to include a reference on the person document only.

Implementing the above scenario is as simple as assigning a _bankAccount_ document's *_id* to a new field in our person document:

Let's first create a bank account:

```js
> db.bankAccounts.insert({
  balance: 2000,
})
```

Now let's get that account's _id_:

```js
> db.bankAccounts.findOne({})
{ "_id" : ObjectId("56426f481779b50ee5267752"), "balance" : 2000 }
```

Now let's insert a person and reference their bank account:

```js
> db.people.insert({
    name: "Miguel",
    age: 46,
    bankAccount: ObjectId("56426f481779b50ee5267752")
})
```

Again, because there are no "joins" in MongoDB, retrieving a person's bank account information would require a separate query on the _bankAccounts_ collection.

```js
> db.bankAccounts.find({ "_id": db.people.findOne({ name: "Miguel" }).bankAccount })
{ "_id" : ObjectId("56426f481779b50ee5267752"), "balance" : 2000 }
```

#### Views 
A view is simply any SELECT query that has been given a name and saved in the database. For this reason, a view is sometimes called a named query or a stored query. To create a view, you use the SQL syntax:

        CREATE OR REPLACE VIEW <view_name> AS
        SELECT <any valid select query>;
The view query itself is saved in the database, but it is not actually run until it is called with another SELECT statement. For this reason, the view does not take up any disk space for data storage, and it does not create any redundant copies of data that is already stored in the tables that it references (which are sometimes called the base tables of the view).
Although it is not required, many database developers identify views with names such as v_Customers or Customers_view. This not only avoids name conflicts with base tables, it helps in reading any query that uses a view.
The keywords OR REPLACE in the syntax shown above are optional. Although you don’t need to use them the first time that you create a view, including them will overwrite an older version of the view with your latest one, without giving you an error message.
The syntax to remove a view from your schema is exactly what you would expect:
        DROP VIEW <view_name>;
Using views
A view name may be used in exactly the same way as a table name in any SELECT query. Once stored, the view can be used again and again, rather than re-writing the same query many times.

The most basic use of a view would be to simply SELECT * from it, but it also might represent a pre-written subquery or a simplified way to write part of a FROM clause.
In many systems, views are stored in a pre-compiled form. This might save some execution time for the query, but usually not enough for a human user to notice.
One of the most important uses of views is in large multi-user systems, where they make it easy to control access to data for different types of users. As a very simple example, suppose that you have a table of employee information on the scheme Employees = {employeeID, empFName, empLName, empPhone, jobTitle, payRate, managerID}. Obviously, you can’t let everyone in the company look at all of this information, let alone make changes to it.
Your database administrator (DBA) can define roles to represent different groups of users, and then grant membership in one or more roles to any specific user account (schema). In turn, you can grant table-level or view-level permissions to a role as well as to a specific user. Suppose that the DBA has created the roles managers and payroll for people who occupy those positions. In Oracle®, there is also a pre-defined role named public, which means every user of the database.
You could create separate views even on just the Employees table, and control access to them like this:
        CREATE VIEW phone_view AS
        SELECT empFName, empLName, empPhone FROM Employees;
        GRANT SELECT ON phone_view TO public;

        CREATE VIEW job_view AS
        SELECT employeeID, empFName, empLName, jobTitle, managerID FROM Employees;
        GRANT SELECT, UPDATE ON job_view TO managers;

        CREATE VIEW pay_view AS
        SELECT employeeID, empFName, empLName, payRate FROM Employees;
        GRANT SELECT, UPDATE ON pay_view TO payroll;
Only a very few trusted people would have SELECT, UPDATE, INSERT, and DELETE privileges on the entire Employees base table; everyone else would now have exactly the access that they need, but no more.
When a view is the target of an UPDATE statement, the base table value is changed. You can’t change a computed value in a view, or any value in a view that is based on a UNION query. You may also use a view as the target of an INSERT or DELETE statement, subject to any integrity constraints that have been placed on the base tables.



Indexes
An index, as you would expect, is a data structure that the database uses to find records within a table more quickly. Indexes are built on one or more columns of a table; each index maintains a list of values within that field that are sorted in ascending or descending order. Rather than sorting records on the field or fields during query execution, the system can simply access the rows in order of the index.

Unique and non-unique indexes: When you create an index, you may allow the indexed columns to contain duplicate values; the index will still list all of the rows with duplicates. You may also specify that values in the indexed columns must be unique, just as they must be with a primary key. In fact, when you create a primary key constraint on a table, Oracle and most other systems will automatically create a unique index on the primary key columns, as well as not allowing null values in those columns. One good reason for you to create a unique index on non-primary key fields is to enforce the integrity of a candidate key, which otherwise might end up having (nonsense) duplicate values in different rows.

Queries versus insertion/update: It might seem as if you should create an index on every column or group of columns that will ever by used in an ORDER BY clause (for example: lastName, firstName). However, each index will have to be updated every time that a row is inserted or a value in that column is updated. Although index structures such as B or B+ trees allow this to happen very quickly, there still might be circumstances where too many indexes would detract from overall system performance. This and similar issues are often covered in more advanced courses.

Syntax: As you would expect by now, the SQL to create an index is:

        CREATE INDEX <indexname> ON <tablename> (<column>, <column>...);
To enforce unique values, add the UNIQUE keyword:

        CREATE UNIQUE INDEX <indexname> ON <tablename> (<column>, <column>...);
To specify sort order, add the keyword ASC or DESC after each column name, just as you would do in an ORDER BY clause.

To remove an index, simply enter:

        DROP INDEX <indexname>;
        
## Overview OF Transactions 
Acid properties in DBMS are a set of principles that guarantee reliable processing of transactions in a database management system (DBMS). ACID stands for Atomicity, Consistency, Isolation, and Durability. Atomicity ensures that a transaction is either executed completely or not at all. Consistency ensures that the database remains in a consistent state before and after a transaction. Isolation ensures that multiple transactions can run concurrently without interfering with each other. Durability ensures that the results of a committed transaction are permanent and cannot be lost due to system failure.

## Introduction to ACID Properties in DBMS
ACID Properties in DBMS ensure consistency and reliability in transactions. For example, when two users try to book the same train ticket, the user who clicks the 'Book Now' button first is given preference. Without ACID Properties, both users could end up with a confirmed ticket, causing problems. ACID Properties prevent errors and maintain consistency, which is crucial when multiple users are trying to book/purchase the same thing.

## What is Database Transaction?
A transaction is a logical unit of work that accesses and updates the contents of a database. Read and write operations are used by transactions to access data. A transaction has several states:

## Transaction State of Acid properties in DBMS

1. Active State: Every transaction starts out in the active state. The transaction is currently being carried out in this state

2. Partially Committed State: A transaction has reached this state when it completes all operations but the data has not been saved to the database

3. Failed State: The transaction is considered to be in the failed state if any of the database recovery system’s checks fail

4. Committed State: If a transaction completes its final operation successfully, it is considered to be committed. In this state, all of the changes are written to memory and as a result, saved on the database system permanently

5. Aborted State: If any of the tests fail, the transaction is said to go to a failed state. Upon entering this state, the database recovery system attempts to bring the database to the previous consistent state(committed state). If this doesn’t happen then the transaction would be rolled back or aborted so as to bring the database back to a consistent state. Once it has been aborted, the database recovery module will either kill the transaction or re-start the transaction

6. Terminated State: If there is no rollback and the transaction is in the “committed state,” the system is consistent and ready for a new transaction, while the old one is terminated

## What are ACID Properties in DBMS?
ACID properties are a set of properties that guarantee reliable processing of transactions in a database management system (DBMS). Transactions are a sequence of database operations that are executed as a single unit of work, and the ACID properties ensure that transactions are processed reliably and consistently in a DBMS.

The Atomicity property ensures that a transaction is either executed completely or not at all. The Consistency property ensures that the database remains in a consistent state before and after a transaction. The Isolation property ensures that multiple transactions can run concurrently without interfering with each other. The Durability property ensures that the results of a committed transaction are permanent and cannot be lost due to system failure.

Together, these properties ensure that transactions are processed reliably and consistently in a DBMS, which is essential for the integrity and accuracy of data in a database.


## 1. Atomicity in DBMS
The term atomicity is the ACID Property in DBMS that refers to the fact that the data is kept atomic. It means that if any operation on the data is conducted, it should either be executed completely or not at all. It also implies that the operation should not be interrupted or just half completed. When performing operations on a transaction, the operation should be completed totally rather than partially. If any of the operations aren’t completed fully, the transaction gets aborted.
Sometimes, a current operation will be running and then, an operation with a higher priority enters. This discontinues the current operation and the current operation will be aborted.

In the example above, if we consider the case that both users get notified that the seat is booked and neither of them is allowed to be seated because only one seat is available on the train, that is a half-fulfilled transaction. The transaction would be complete if they were able to be seated as well. Instead, according to atomicity, the person who clicks the button first books the seat and gets the notification of having purchased a ticket, and the seats left are updated. The second person’s transaction is rolled back and they are notified that no more seats are available. Let us consider an easier example where one person is trying to book a ticket. They were able to select their seat and reach the payment gateway. But, due to bank server issues, the payment could not go through. Does this mean that their booked seat will be reserved for them?
No. This is because one full transaction means reserving your seat and paying for it as well. If any of the steps fail, the operation will be aborted and you will be brought back to the initial state.

Atomicity in DBMS is often referred to as the ‘all or nothing’ rule.


## 2. Consistency in DBMS
This ACID Property will verify the total sum of seats left in the train+sum of seats booked by users=total the number of seats present in the train. After each transaction, consistency is checked to ensure nothing has gone wrong.

Let us consider an example where one person is trying to book a ticket. They are able to reserve their seat but their payment hasn’t gone through due to bank issues. In this case, their transaction is rolled back. But just doing that isn’t sufficient. The number of available seats must also be updated. Otherwise, if it isn’t updated, there will be an inconsistency where the seat given up by the person is not accounted for. Hence, the total sum of seats left in the train + the sum of seats booked by users would not be equal to the total number of seats present in the train if not for consistency.



## 3. Isolation in DBMS
Isolation is defined as a state of separation. Isolation is an ACID Property in DBMS where no data from one database should impact the other and where many transactions can take place at the same time. In other words, when the operation on the first state of the database is finished, the process on the second state of the database should begin. It indicates that if two actions are conducted on two different databases, the value of one database may not be affected by the value of the other. When two or more transactions occur at the same time in the case of transactions, consistency should be maintained. Any modifications made in one transaction will not be visible to other transactions until the change is committed to the memory.



## 4. Durability in DBMS
The ACID Property durability in DBMS refers to the fact that if an operation is completed successfully, the database remains permanent in the disk. The database’s durability should be such that even if the system fails or crashes, the database will survive. However, if the database is lost, the recovery manager is responsible for guaranteeing the database’s long-term viability. Every time we make a change, we must use the COMMIT command to commit the values.


## SQL Developer using the SQL Developer 

Downloading and Installing SQL Developer
SQL Developer can be downloaded for free from the Oracle Developer’s network. SQL Developer requires a Java Development Kit in order to run. For example, SQL Developer version 4.1.3 and later requires JDK 1.8.

Visit the following link to download the SQL Developer files:

http://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html



Configuring a new Database Connection
The first order of business is to create a new Connection to your Oracle database. To set up a new connection you will need to know:

The name (or IP address) of the server that is running Oracle. If you have installed Oracle on your local computer, then it is likely you can use the “localhost” (or 127.0.01).
The TCP/IP port number where the Oracle Listener process is running. The default for Oracle is to use port 1521. Unless you have configured this differently, use 1521.
The Oracle System Identifier (SID) or Service Name that identifies the specific Oracle instance on the server.
Some common combinations might be:

Oracle 11g or 12c Enterprise Edition installed on the same (local) server or PC: Host: localhost, Port: 1521, SID: orcl
Oracle 11g Express Edition installed on the same (local) server or PC: Host: localhost, Port: 1521, SID: xe
Oracle 11g or 12c Enterprise Edition installed on the remote server: Host: myhostname.domain.com, Port: 1521, SID: orcl
Oracle 12c Enterprise Edition installed on the remote server using Multi-tenant database: Host: myhostname.domain.com, Port: 1521, Service Name: pdb1
Oracle Autonomous Data Warehouse or Autonomous Transaction Processing database running Oracle Cloud: Change the Connection Type to Cloud Wallet and then select your wallet .zip file that downloaded from your cloud database instance. Follow these instructions (Page 6).
Note that if your target DBMS is an Autonomous Database in Oracle Cloud, you will need to follow slightly different instructions that make use of the Oracle Cloud Wallet. Follow these instructions (Page 6) on setting up a connection to an autonomous Database.

To get started configuring the new connection, click on the down arrow next to the green + sign and select New Connection…



The default “New / Select Database Connection” window will appear.




Give a new name for your connection and fill in the username and password for the Oracle database account you wish to connect to.

Fill in the Hostname with the internet host name or IP address of the server where Oracle database is running. Set the port to match where the Oracle Listener is running (1521 is the typical default).

If the host has an Oracle System Identifier (SID) set, type that in. Otherwise, if the Oracle server is using multi-tenant (via oracle 12c or newer) then select Service Name and supply the service name for the database instance.

Other advanced authentication, encryption and security settings can then be specific if necessary.

Below is an example of connecting to an Oracle 12c instance on the local server using the Oracle system account. The password for this account was set up during the database installation.




Typical Login errors and things to check
There are a number of reasons why SQL Developer may not make a successful connection to the Oracle Server. Some of the more common potential problems and solutions are listed below. Keep in mind the “Client/Server” Oracle architecture and the fact that there is a network between them.

Status : Failure -Test failed: IO Error: The Network Adapter could not establish the connection
There is an issue connecting over the network between the SQL Developer client and the Oracle database server. Either the Host name (or IP Address), or Port number is incorrect. Or some other network problem (DNS, Firewall, etc.) is preventing SQL Developer from connecting to the Oracle server. It is also possible that the Oracle Listener (the network service that accepts incoming connections) is not running or is listening to a different network port. Try to use traceroute (tracert on Windows) to see if the server can be reached at all. Verify that the Oracle Database is up and running along with the Oracle Listener service and that no firewalls are blocking connections to port 1521.

Status : Failure -Test failed: Listener refused the connection with the following error:
ORA-12505, TNS:listener does not currently know of SID given in connect descriptor
SQL Developer is connecting successfully to the Oracle server Listener process, however the SID provided does not match what is configured on the database server.

Status : Failure -Test failed: Listener refused the connection with the following error:
ORA-12514, TNS:listener does not currently know of service requested in connect descriptor
SQL Developer is connecting successfully to the Oracle server, however the Service Name provided does not match what is configured on the database server.

Status : Failure -Test failed: ORA-01017: invalid username/password; logon denied
SQL Developer is connecting successfully to the Oracle server, and to the instance (so hostname, port and SID or Service Name are correct). However the username and/or password do not match.

Status : Failure -Test failed: ORA-28000: the account is locked
SQL Developer is connecting successfully to the Oracle server, and to the instance (so hostname, port and SID or Service Name are correct). However the Oracle account has been locked (e.g., too many failed login attempts or password has expired).

ORA-12518: TNS:listener could not hand off client connection
SQL Developer is connecting successfully to the Oracle server and to the instance (so hostname, port and SID or Service Name are correct). However the listener in turn can not make a connection to the Oracle database. This can happen if the database is not running or opened, or if the server running Oracle is running out of RAM. It can also happen if there is a user permissions problem between the listener process and the database processes.




## CRUD Operations in Java using JDBC:
CRUD is the acronym for the following four operations.

* C- INSERTION
* R- RETRIEVAL
* U- UPDATION
* D- DELETION


Insert Operation using JDBC in Java:
The following JDBC APPLICATION is used to store 2 account information (accno, name, and balance) in the Account table.

    import java.sql.*;
    class AccountStoringApplication
    {
        public static void main(String[] args) throws ClassNotFoundException, SQLException
        {
         Class.forName("oracle.jdbc.driver.OracleDriver");
         Connection con = DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","System", "pranaya");
         Statement st = con.createStatement();
            int c = st.executeUpdate("insert into account values(1005, 'pranaya', 2345)");
            System.out.println(c + "account stored successfully");
            int c = st.executeUpdate("insert into account values(1006, 'kumar', 5345)");
            System.out.println(c + "" more account stored successfully");
            st.close();
            con.close();
        }
    }
Update Operations using JDBC in Java:
The following JDBC APPLICATION is used to update the accounts by adding Rs 2000 to each account in the Account table. The SQL statement for updating is: update account set balance = balance+2000

    import java.sql.*;
    class UpdateAccountApplication 
    {
        public static void main (String[]args) throws ClassNotFoundException, SQLException 
        {
            Class.forName ("oracle.jdbc.driver.OracleDriver");  
            Connection con = DriverManager.getConnection ("jdbc:oracle:thin:@localhost:1521:xe", "System", "pranaya");  
            Statement st = con.createStatement ();
            int rows = st.executeUpdate ("update account set balance = balance+2000");
            System.out.println (rows + " rows modified");    
            st.close ();    
            con.close ();
        } 
    }
Delete Operations using JDBC in Java:
The following JDBC APPLICATION is used to delete the account and if the account does not exist then show the same. Here, we need to enter the account number at runtime. The SQL statement is “delete from account where accno =” + ano

    import java.sql.*;
    import java.util.*;
    class AccountCloseApplication 
    {
        public static void main (String[]args) throws ClassNotFoundException, SQLException 
        {  
            Scanner sc = new Scanner (System.in);  
            System.out.println ("ENTER ACCOUNT NUMBER");   
            int ano = sc.nextInt ();    
            Class.forName ("oracle.jdbc.driver.OracleDriver");    
            Connection con = DriverManager.getConnection ("jdbc:oracle:thin:@localhost:1521:xe", "System", "pranaya");    
            Statement st = con.createStatement (); 
            int c = st.executeUpdate ("delete from account where accno =" + ano);
            if (c == 0)    
                System.out.println ("account doesnot exist");  
            else
                System.out.println ("account closed successfully");
            st.close ();   
            con.close (); 
        } 
    }
`
In the above three cases means for Insertion, Updation, and Deletion, the DBMS returns an integer number. In the case of INSERT if the record is successfully inserted into the database then DBMS returns 1. In the case of UPDATE if the record is successfully updated then it returns the no i.e. updated number of records. And in the case of DELETE, it returns 1 if the successful record is deleted else it returns 0. But in the case of retrieval, it is different.

How to retrieve the data from a Database in JDBC Application?
In order to understand this, please have a look at the following image.