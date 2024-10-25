 # **JOINS**

A *JOIN* clause is used to combine rows from two or more tables, based on a related column between them.

## Different Types of Joins

*INNER JOIN:* Returns records that have matching values in both tables

*LEFT JOIN:* Returns all records from the left table, and the matched records from the right table

*RIGHT JOIN:* Returns all records from the right table, and the matched records from the left table

*FULL JOIN:* Returns all records when there is a match in either left or right table

*INNER JOIN*

The INNER JOIN keyword selects records that have matching values in both tables.

# ACID Properties

**A – Atomicity**

Atomicity requires transactions to be treated as a single "unit of work." The entire sequence of transaction operations succeeds or fails as one entity. There is no partial success or failure.  

For example, transferring money from one bank account involves multiple steps:

Debit amount X from Account A 
Credit amount X to Account B
As per atomicity, either all debit and credit operations succeed or they all fail. If the debit succeeds, but the credit fails for any reason, the entire transaction is rolled back. Atomicity ensures there are no partial or incomplete transactions.

Atomicity prevents unwanted data updates from unconcluded transactions. Without it, the debit may persist while the credit fails, causing data inconsistency. By reverting partial transactions, atomicity keeps the database consistent.

**C – Consistency**

The consistency property ensures that only valid data is written to the database. Before committing a transaction, consistency checks are performed to maintain database constraints and business rules.

For example, a transaction crediting 5000 to a bank account with a current balance of 3000 is invalid if the account has an overdraft limit of 1000. The transaction violates consistency by exceeding the permissible account limit. Hence, it is blocked and aborted.

Consistency enforcement prevents data corruption and invalid entries. Only transactions abiding by consistency rules are committed to upholding data accuracy. Real-world business constraints are modeled into the database via consistency.

**I – Isolation**

Isolation maintains the independence of database transactions. Uncommitted transactions are isolated with locking mechanisms to prevent dirty reads or lost updates.  

For instance, if Transaction T1 updates a row, Transaction T2 must wait until T1 commits or rolls back. Isolation prevents T2 from reading unreliable data updated by T1 but not committed yet.

Isolation avoids concurrency issues like:

Dirty reads - Reading uncommitted data from other transactions
Lost updates - Overwriting another transaction's uncommitted updates 
Non-repeatable reads - Same query yielding different results across transactions
By isolating transactions, consistency is maintained despite concurrent execution and updates. Changes remain isolated until permanent.

**D – Durability**

Durability provides persistence guarantees for committed transactions. The system upholds the changes once a transaction is committed even if it crashes later. Durability is achieved with database backups, transaction logs, and disk storage.

For example, if a transaction updates a customer's address, durability ensures the updated address is not lost due to a hard disk failure or power outage. The change will persist with the help of storage devices, backups, and logs.

Durability ensures that transactions, once committed, will survive permanently. Failed hardware, power loss, and even database crashes will not undo committed transactions due to durability support.


# What is Database Normalization? #

Database normalization is a database design principle for organizing data in an organized and consistent way.

It helps you avoid redundancy and maintain the integrity of the database. It also helps you eliminate undesirable characteristics associated with insertion, deletion, and updating.

## What is the Purpose of Normalization? ##

The main purpose of database normalization is to avoid complexities, eliminate duplicates, and organize data in a consistent way. In normalization, the data is divided into several tables linked together with relationships.

Database administrators are able to achieve these relationships by using primary keys, foreign keys, and composite keys.

To get it done, a primary key in one table, for example, employee_wages is related to the value from another table, for instance, employee_data.

**N.B.:** A **primary key** is a column that uniquely identifies the rows of data in that table. It’s a unique identifier such as an *employee ID, student ID, voter’s identification number (VIN),* and so on.

A **foreign key** is a field that relates to the primary key in another table.

A **composite key** is just like a primary key, but instead of having a column, it has multiple columns.

## Types of normalization ##

## 1. First normal form (1NF)
- Eliminate repeating groups in individual tables.
- Create a separate table for each set of related data.
- Identify each set of related data with a primary key.

## 2. Second normal form (2NF)
The 1NF only eliminates repeating groups, not redundancy. That’s why there is 2NF.
A table is said to be in 2NF if it meets the following criteria:
it’s already in 1NF
has no partial dependency. That is, all non-key attributes are fully dependent on a primary key.

## 3. Third normal form (3NF)
When a table is in 2NF, it eliminates repeating groups and redundancy, but it does not eliminate transitive partial dependency.  
This means a non-prime attribute (an attribute that is not part of the candidate’s key) is dependent on another non-prime attribute. This is what the third normal form (3NF) eliminates.  
So, for a table to be in 3NF, it must:  
- be in 2NF
- have no transitive partial dependency.

## 4. Fourth normal form (4NF)
The Fourth Normal Form (4NF) is a level of database normalization where there are no non-trivial multivalued dependencies other than a candidate key. It builds on the first three normal forms (1NF, 2NF, and 3NF) and the Boyce-Codd Normal Form (BCNF). It states that, in addition to a database meeting the requirements of BCNF, it must not contain more than one multivalued dependency.  
### Properties  
A relation R is in 4NF if and only if the following conditions are satisfied: 
1. It should be in the Boyce-Codd Normal Form (BCNF).
2. The table should not have any Multi-valued Dependency.  

A table with a multivalued dependency violates the normalization standard of the Fourth Normal Form (4NF) because it creates unnecessary redundancies and can contribute to inconsistent data. To bring this up to 4NF, it is necessary to break this information into two tables. 

## 5. Boyce-Codd Normal Form (BCNF)
Boyce–Codd Normal Form (BCNF) is based on functional dependencies that take into account all candidate keys in a relation; however, BCNF also has additional constraints compared with the general definition of 3NF.  

### Rules for BCNF
- Rule 1: The table should be in the 3rd Normal Form.  

- Rule 2: X should be a superkey for every functional dependency (FD) X−>Y in a given relation.  

Note: To test whether a relation is in BCNF, we identify all the determinants and make sure that they are candidate keys.